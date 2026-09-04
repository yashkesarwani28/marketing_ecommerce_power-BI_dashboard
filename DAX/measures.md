# DAX Measures

Documented measures from the Power BI data model, grouped by dashboard area.

---

## Revenue & Orders

```dax
Total Revenue = SUM(transactions[gross_revenue])
```

```dax
Total Orders = DISTINCTCOUNT(transactions[transaction_id])
```

```dax
Average Order Value = DIVIDE([Total Revenue], [Total Orders])
```

---

## Funnel & Conversion

```dax
Visitors = 
CALCULATE(
    COUNT('events (2)'[event_id]),
    'events (2)'[event_type] = "view"
)
```

```dax
Purchases = 
CALCULATE(
    COUNT('events (2)'[event_id]),
    'events (2)'[event_type] = "purchase"
)
```

```dax
Conversion Rate = DIVIDE([Purchases], [Visitors]) * 100
```

---

## Session Behavior

```dax
Formatted Session Durations = 
VAR totalSeconds = AVERAGE('events (2)'[session_duration_sec])
VAR minutes = INT(totalSeconds / 60)
VAR seconds = MOD(totalSeconds, 60)
RETURN 
minutes & " mins " & FORMAT(seconds, "00") & " secs"
```

---

## Refunds

```dax
Refund Orders = 
CALCULATE(
    COUNT(transactions[transaction_id]),
    transactions[refund_flag] = "Yes"
)
```

```dax
Refund Rate = DIVIDE([Refund Orders], [Total Orders]) * 100
```

```dax
Refund Target = 0.05
```

```dax
Refund Max Value = 1
```

> `Refund Target` and `Refund Max Value` are static constants used to set the target line and axis max on the Refund Rate gauge visual (Transaction & Geographical Revenue Analysis page).

---

## Campaigns

```dax
Average Uplift = AVERAGE(campaigns[expected_uplift])
```

```dax
> Active Campaigns = 
> CALCULATE(
>     COUNT(campaigns[campaign_id]),
>     campaigns[end_date] >= MIN(campaigns[end_date])
> )
> ```

---

