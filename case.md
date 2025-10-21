---
layout: home
title: Case
---

- Multiple conditions with multiple outcomes (if, elseif, then)

## Basic example

```KQL
table_name
| where ColumnName1 == "string1"
| extend NewColumnName1 = case(ColumnName2 > 10, "Danger",
                               ColumnName2 > 30, "Will Robinson",
                               ColumnName2 > 50, "Run for the hills",
                               "All is well."
                              )
| project ColumnName3,
          ColumnName1,
          ColumnName2,
          NewColumnName1
| sort by ColumnName2
```

## Alternate formatting

```KQL
table_name
| where ColumnName1 == "string1"
| project ColumnName3,
          ColumnName1,
          ColumnName2,
          NewColumnName1 = case(ColumnName2 < 10, "Danger", ColumnName2 < 30, "Will Robinson", ColumnName2 < 50, "Run for the hills", "All is well." )
| sort by ColumnName2
```

## Summarizing

```KQL
table_name
| where ColumnName1 == "string1"
| extend NewColumnName1 = case(ColumnName2 > 10, "Danger",
                               ColumnName2 > 30, "Will Robinson",
                               ColumnName2 > 50, "Run for the hills",
                               "All is well."
                              )
| Summarize ColumnName3=count() by NewColumnName1
```

## Dates not this way

```KQL
table_name
| where ColumnName1 == "string"1" and ColumnName2 > 0
| where TimeColumnName1 >= startofyear(now())
| project TimeColumnName1,
          ColumnName3
| extend MonthNumber = datetime_part("month", TimeColumnName1),
         YearNumber  = datetime_part("year", TimeColumnName1),
         MonthName   = case(datetime_part("month", TimeColumnName1) == 1,  "Jan",
                            datetime_part("month", TimeColumnName1) == 2,  "Feb",
                            datetime_part("month", TimeColumnName1) == 3,  "Apr",
                            datetime_part("month", TimeColumnName1) == 4,  "Mar",
                            datetime_part("month", TimeColumnName1) == 5,  "May",
                            datetime_part("month", TimeColumnName1) == 6,  "Jun",
                            datetime_part("month", TimeColumnName1) == 7,  "Jul",
                            datetime_part("month", TimeColumnName1) == 8,  "Aug",
                            datetime_part("month", TimeColumnName1) == 9,  "Sep",
                            datetime_part("month", TimeColumnName1) == 10, "Oct",
                            datetime_part("month", TimeColumnName1) == 11, "Nov",
                            datetime_part("month", TimeColumnName1) == 12, "Dec",
                            "Unknown Month" // Always include a default even if it should never happen
                           )
| summarize MonthCount = count()
          by ColumnName3, YearNumber, MonthNumber, MonthName
| project ColumnName3,
          MonthCount,
          YearNumber,
          MonthNumber,
          YearText = strcat(YearNumber) // Returns as string not integer (removes comma on display)
          MonthName,
          MonthYear = strcat(MonthName, " ", YearNumber),
          YearMonth = strcat(YearNumber, " - ", MonthName)
| sort by ColumnName3, YearNumber, MonthNumber
```

## Dates the right way

```KQL
table_name
| where ColumnName1 == "string1" and ColumnName2 > 0
| where TimeColumnName1 >= startofyear(now())
| project TimeColumnName1,
          ColumnName3
| extend MonthNumber = datetime_part("month", TimeColumnName1),
         YearNumber  = datetime_part("year", TimeColumnName1),
| extend MonthName   = case(MonthNumber == 1,  "Jan",
                            MonthNumber == 2,  "Feb",
                            MonthNumber == 3,  "Apr",
                            MonthNumber == 4,  "Mar",
                            MonthNumber == 5,  "May",
                            MonthNumber == 6,  "Jun",
                            MonthNumber == 7,  "Jul",
                            MonthNumber == 8,  "Aug",
                            MonthNumber == 9,  "Sep",
                            MonthNumber == 10, "Oct",
                            MonthNumber == 11, "Nov",
                            MonthNumber == 12, "Dec",
                            "Unknown Month"  // Always include a default even if it should never happen
                           )
| summarize MonthCount = count()
          by ColumnName3, YearNumber, MonthNumber, MonthName
| project ColumnName3,
          MonthCount,
          YearNumber,
          MonthNumber,
          YearText = strcat(YearNumber) // Returns as string not integer (removes comma on display)
          MonthName,
          MonthYear = strcat(MonthName, " ", YearNumber),
          YearMonth = strcat(YearNumber, " - ", MonthName)
| sort by ColumnName3, YearNumber, MonthNumber
```
