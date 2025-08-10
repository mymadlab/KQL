# Startof

-  Set of operators that allow you to select the start of a time period (day, year, etc.)

## Basics of startof

```KQL
table_name
| where TimeColumnName1 >= startofyear(now())
| extend DayGenerated = startofday(TimeColumnName1)
| project TimeColumnName1,
          DayGenerated,
          ColumnName1,
          ColumnName2,
          ColumnName3
```

## Calculating startof last year

```KQL
print startofyear(ago(365d))
```

## Calculating startof two years from now

```KQL
print startofyear(now(730d))
```

## Summarizing Log Count by StartOfDay

```KQL
table_name
| where TimeColumnName1 >= startofyear(now())
| extend DayGenerated = startofday(TimeColumnName1)
| project TimeColumnName1,
          DayGenerated,
          ColumnName1,
| summarize LogCount = count()
            by DayGenerated,
               ColumnName1
| sort by ColumnName1 asc,
          DayGenerated asc
```

## Summarizing Log Count by StartOfMonth

```KQL
table_name
| where TimeColumnName1 >= startofyear(now())
| extend DayGenerated = startofmonth(TimeColumnName1)
| project TimeColumnName1,
          DayGenerated,
          ColumnName1,
| summarize LogCount = count()
            by DayGenerated,
               ColumnName1
| sort by ColumnName1 asc,
          DayGenerated asc
```

## Summarizing Log Count by StartOfYear

```KQL
table_name
| where TimeColumnName1 >= startofyear(now())
| extend DayGenerated = startofyear(TimeColumnName1)
| project TimeColumnName1,
          DayGenerated,
          ColumnName1,
| summarize LogCount = count()
            by DayGenerated,
               ColumnName1
| sort by ColumnName1 asc,
          DayGenerated asc
```

## Summarizing Log Count by StartOfWeek

```KQL
table_name
| where TimeColumnName1 >= startofyear(now())
| extend DayGenerated = startofweek(TimeColumnName1)
| project TimeColumnName1,
          DayGenerated,
          ColumnName1,
| summarize LogCount = count()
            by DayGenerated,
               ColumnName1
| sort by ColumnName1 asc,
          DayGenerated asc
```
