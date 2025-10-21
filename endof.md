---
layout: home
title: Endof
---

# Endof

-  Set of operators that allow you to select the end of a time period (day, year, etc.)

## Basics of endof

```KQL
table_name
| where TimeColumnName1 >= startofyear(now())
| extend DayGenerated = endofday(TimeColumnName1)
| project TimeColumnName1,
          DayGenerated,
          ColumnName1,
          ColumnName2,
          ColumnName3
```
## Examples of various EndOf

```KQL
print EndOfYear         = endofyear(now())
      EndOfLastYear     = endof(ago(365d))
      EndOfCurrentMonth = endof(now())
      EndOfCurrentDay   = endof(now())
      EndOfCurrentWeek  = endof(now())
      EndOfLastWeek     = endof(ago(7d))
      EndOfNextWeek     = endof(now(7d))
```

## Summarizing Log Count by EndOfDay

```KQL
table_name
| where TimeColumnName1 >= startofyear(now())
| extend DayGenerated = endofday(TimeColumnName1)
| project TimeColumnName1,
          DayGenerated,
          ColumnName1,
| summarize LogCount = count()
            by DayGenerated,
               ColumnName1
| sort by ColumnName1 asc,
          DayGenerated asc
```

