# Datetime_part

- Extracts the individual part of a datetime part returning a integer.

## Basic Example

```KQL
table_name
| project TimeColumnName1,
          year        = datetime_part("year", TimeColumnName1),
          quarter     = datetime_part("quarter", TimeColumnName1),
          month       = datetime_part("month", TimeColumnName1),
          weekOfYear  = datetime_part("week_of_year", TimeColumnName1),
          day         = datetime_part("day", TimeColumnName1),
          dayOfYear   = datetime_part("dayOfYear", TimeColumnName1),
          hour        = datetime_part("hour", TimeColumnName1),
          minute      = datetime_part("minute", TimeColumnName1),
          second      = datetime_part("second", TimeColumnName1),
          millisecond = datetime_part("millisecond", TimeColumnName1),
          microsecond = datetime_part("microsecond", TimeColumnName1),
          nanosecond  = datetime_part("nanosecond", TimeColumnName1),
          ColumnName1,
          ColumnName2
```
## How many records generated per hour of day

```KQL
table_name
| where TimeColumnName1 => ago(7d)
| extend HourOfDay = datetime_part("hour", TimeColumnName1)
| project HourOfDay
| summarize TableNameCount=count()
            by HourOfDay
| sort by HourOfDay asc
```
