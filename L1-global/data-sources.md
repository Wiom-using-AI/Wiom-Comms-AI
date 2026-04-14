# Data Sources — Wiom Comms AI

## FILE PURPOSE
Tables, columns, filters, and query patterns the measurement agent
needs to write SQL queries for comms measurement. This file is a
comms-focused subset of the full Wiom data dictionary.

## WHEN TO USE
Loaded by the measurement agent when constructing measurement queries
(Mode B). Also useful for the design agent when specifying data sources
in Section 6 of a comms brief.

## HOW TO USE
- Match the metric type to the correct data source section below
- Use the provided filters exactly. Do not invent new filters.
- All timestamps are UTC in Snowflake. Always convert to IST.
- All queries run through the Metabase API, not direct Snowflake.

## LAST UPDATED
2026-04-13 — v1.0 — initial version. Subset of Wiom data dictionary
relevant to comms measurement.
Maintained by: human

---

## Database and Access

  Database      : PROD_DB (Snowflake)
  Primary schema: PROD_DB.PUBLIC
  BI tool       : Metabase (https://metabase.wiom.in)
  DB ID         : 113 (PROD_DB)
  Auth          : x-api-key header (key stored externally)

### Running a query via Metabase API

```bash
API_KEY=$(cat metabase_key.txt)
curl -s -X POST "https://metabase.wiom.in/api/dataset" \
  -H "Content-Type: application/json" \
  -H "x-api-key: $API_KEY" \
  -d '{
    "database": 113,
    "type": "native",
    "native": {
      "query": "YOUR SQL HERE"
    }
  }'
```

### IST Conversion (mandatory for all date logic)

```sql
-- UTC timestamp to IST date:
TO_DATE(DATEADD(minute, 330, <timestamp_column>))

-- Current date in IST:
CAST(DATEADD(minute, 330, CURRENT_TIMESTAMP()) AS DATE)
```

---

## Partner-Level Data

### HIERARCHY_BASE
Partner hierarchy with geography. Use for all partner filtering.

  Key columns:
    PARTNER_ACCOUNT_ID   : unique partner identifier
    cluster              : geography cluster
    MIS_CITY             : city
    ZONE, ZONE_DETAILED  : zone breakdown
    DEDUP_FLAG           : always filter = 1
    PARTNER_STATUS       : status (Active, etc.)
    PARTNER_NAME         : partner name
    PARTNER_MOBILE       : partner mobile

  Mandatory filter: DEDUP_FLAG = 1

  City mapping:
    CASE WHEN cluster = 'Delhi' THEN 'Delhi'
         WHEN cluster = 'Mumbai' THEN 'Mumbai'
         ELSE 'Bharat' END AS city

### partner_details_log
Daily partner status snapshot. One full snapshot per day.

  Key columns:
    lco_id_long    : partner ID (matches PARTNER_ACCOUNT_ID via idmaker)
    status         : ACTIVE / TERMINATION / CLOSED / TEMPORARY SUSPENSION
    added_time     : snapshot date
    city, zone     : geography

  CRITICAL: Snapshot table. Always filter to a single date:
    DATE("added_time") = :target_date
  Querying across multiple dates multiplies counts.

  Active filter: "status" = 'ACTIVE'
  Column names are lowercase, must quote: "status", "added_time"

### supply_model
Partner status model.

  Key columns:
    PARTNER_ACCOUNT_ID  : partner ID
    partner_status      : Active / Inactive
    PARTNER_ONBOARDING_DATE : when partner joined

  Active filter: partner_status IN ('Active')

---

## Transaction and Recharge Data

### t_router_user_mapping
Core transaction table. Each row = a device registration/recharge.

  Key columns:
    transaction_id  : unique transaction
    mobile          : customer mobile
    router_nas_id   : NAS ID
    charges         : amount charged
    selected_plan_id: plan selected
    created_on      : timestamp (UTC)
    created_by      : partner who created this
    store_group_id  : 0 = Home, 1 = Wiom Net

  FP (first-pay) filter:
    device_limit='10' AND otp='DONE' AND mobile>'5999999999'
    AND store_group_id=0

  Date (IST): TO_DATE(DATEADD(minute, 330, created_on))

### wiomBillingWifi
Payment records matched to transactions.

  Key columns:
    transaction_id : matches t_router_user_mapping
    mobile         : customer mobile
    total_price    : amount
    paymentStatus  : 1 = success
    payment_type   : payment method
    createDate     : timestamp

  Valid payment filter:
    total_price >= 299 AND paymentStatus = 1
    AND mobile > '5999999999'
    AND transaction_id NOT LIKE 'mr%'
    AND payment_type <> 2
    AND (refund_status <> 1 OR refund_status IS NULL)

---

## Service and Quality Data

### service_ticket_model
Support tickets with SLA tracking.

  Key columns:
    ticket_id              : unique ticket
    ticket_type_final      : ticket type
    cx_px                  : Cx (customer) or Px (partner)
    last_title             : ticket description
    ticket_added_time      : creation timestamp
    final_resolved_time    : resolution timestamp
    resolution_tat_bucket  : 'within TAT' or not
    CURRENT_partner_account_id : partner responsible

  SLA targets by type:
    Type 3: 4hr working hours (11AM-9PM IST)
    Type 1: 21 days
    Type 2: 3 days
    Type 4: 1 day

  Within TAT filter: resolution_tat_bucket = 'within TAT'

### PARTNER_INFLUX_SUMMARY
Partner uptime/ping data for quality scoring.

  Key columns:
    partner_id             : partner identifier
    TOTAL_PINGS_RECEIVED   : actual pings
    TOTAL_EXPECTED_PINGS   : expected pings
    appended_date          : date (actual date = appended_date - 1)

  Uptime calc: TOTAL_PINGS_RECEIVED / TOTAL_EXPECTED_PINGS

---

## Task and Installation Data

### taskvanilla_audit
Installation and dispatch audit trail.

  Key columns:
    mobile         : customer mobile
    event_name     : event type
    added_time     : timestamp
    account_id     : partner lng_id
    KEY            : task identifier

  Install completed: event_name = 'OTP_VERIFIED' AND mobile > '5999999999'
  Dispatch sent:     event_name = 'NOTIF_SENT'
  Declined:          event_name = 'DECLINED'

---

## Partner Financial Data

### t_account_balance_sheet1
Partner wallet transactions.

  Key columns:
    transaction_id : unique transaction
    account_id     : partner account
    balance        : current balance
    action         : transaction type
    remark         : description
    added_time     : timestamp

  Commission added:  action = 'COMMISSION_ADDED'
  Withdrawal:        action = 'AMOUNT_WITHDRAWN'

---

## PTL / Call Data

### tata_ivr_events
IVR call events (Partner Talk Line measurement).

  Key columns:
    direction   : inbound / outbound
    status      : answered / missed
    added_time  : timestamp

  Inbound filter: direction = 'inbound'
  Missed filter:  status = 'missed'

  Use for: PTL call volume baseline and spike detection.
  Primary measurement for CSP migration success.

---

## Reference Tables

### CALENDAR
Date dimension with sprint metadata.

  Key columns:
    DATE           : calendar date
    day_of_sprint  : day number within sprint
    sprint_number  : 0 = current, 1 = previous
    sprint_start   : sprint start date
    DAY_NAME       : Monday, Tuesday, etc.

  Join: metric_table.dt = DATE(calendar."DATE")

### t_plan_configuration
Plan metadata.

  Key columns:
    id             : plan ID (matches selected_plan_id)
    time_limit     : validity in seconds
    NAME           : plan name (contains price)
    speed_limit_mbps : speed

  Validity in days: ROUND(time_limit / 60 / 60 / 24)
  M+ plans: >= 28 days
  PayG/STP: < 28 days

---

## Utility Functions

### idmaker (Snowflake UDF)
Creates composite LNG IDs from shard + type + id:

```sql
-- NAS ID (type 0):
prod_db.public.idmaker(shard, 0, nasid)

-- Account ID (type 4):
prod_db.public.idmaker(shard, 4, account_id)
```

### City mapping
```sql
CASE WHEN cluster = 'Delhi' THEN 'Delhi'
     WHEN cluster = 'Mumbai' THEN 'Mumbai'
     ELSE 'Bharat' END AS city
```

### Triple dedup (for FP transaction counting)
```sql
ROW_NUMBER() OVER (PARTITION BY transaction_id ORDER BY id) AS rn1,
ROW_NUMBER() OVER (PARTITION BY mobile, router_nas_id, charges,
  TO_DATE(created_on) ORDER BY id) AS rn2,
ROW_NUMBER() OVER (PARTITION BY mobile, router_nas_id, charges,
  TO_DATE(created_on), TO_DATE(otp_issued_time) ORDER BY id) AS rn3
-- Then filter: WHERE rn1=1 AND rn2=1 AND rn3=1
```

---

## Comms Measurement: Metric-to-Table Mapping

Use this mapping when constructing queries for comms measurement plans.

  METRIC TYPE                    PRIMARY TABLE              NOTES
  -------------------------------------------------------------------
  PTL call volume / spike        tata_ivr_events            Inbound calls, daily count
  Partner active status          partner_details_log        Snapshot table, single date
  Partner geography breakdown    HIERARCHY_BASE             DEDUP_FLAG = 1
  Installation completion        taskvanilla_audit          OTP_VERIFIED events
  Recharge / FP transactions     t_router_user_mapping      With triple dedup
  Payment success                wiomBillingWifi            paymentStatus = 1
  Service ticket volume          service_ticket_model       cx_px filter
  SLA compliance                 service_ticket_model       resolution_tat_bucket
  Partner uptime / quality       PARTNER_INFLUX_SUMMARY     Pings ratio
  Partner wallet / earnings      t_account_balance_sheet1   COMMISSION_ADDED
  App behaviour (popup, video,   CleverTap events           Not in Snowflake.
    quiz, app_opened)                                       Query via CleverTap API
                                                            or exported event tables
                                                            if synced to Snowflake.

---

*data-sources.md — L1-global — v1.0*
*Maintained by: human*
*Do not modify without updating CHANGELOG.md*
