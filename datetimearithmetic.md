# Date/Time Arithmetic

## How long ago (subtraction)

```KQL
table_name
| where ColumnName1 == "string1"
| where TimeColumnName1 > ago(1d)
| extend RightNow = now()
| project TimeColumnName1,
          RightNow,
					HowLongAgo = (RightNow - TimeColumn),
					ColumnName2
```

## With datetime function

```KQL
table_name
| where ColumnName1 == "string1"
| where TimeColumnName1 > ago(1d)
| extend RightNow = now(),
          TimeSinceNewServices = (TimeColumnName1 - datetime(2022-11-03))
| project TimeColumnName1,
          RightNow,
					HowLongAgo = (RightNow - TimeColumn),
					TimeSinceNewServices,
					ColumnName2
```

## Determine number of time units

```KQL
table_name
| where ColumnName1 == "string1"
| where TimeColumnName1 > ago(1d)
| extend TimeSinceStartOfYear = (TimeColumnName1 - datetime(2022-01-01 10:42:33.000 AM)),
         TimeSinceStartOfYearNumberOfHours = (TimeSinceStartOfYear / 1h)
```
