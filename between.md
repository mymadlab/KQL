# Between

- Used to determine if datetime/number is between two other datetimes/numbers

## Between with Dynamic Dates last 7 Days

```KQL
table_name
| where ColumnName1 == "string1"
| where TimeColumnName1 between(ago(7d) .. now())
| project TimeColumnName1,
          ColumnName1,
          ColumnName2
```

## Start of current month to today

```KQL
table_name
| where ColumnName1 == "string1"
| where TimeColumnName1 between(startofmonth(now()) .. now())
| project TimeColumnName1,
          ColumnName1,
          ColumnName2
```

## Calculating previous time periods

```KQL
print StartOfYesterday = startofday(ago(1d)),
      EndOfYesterday   = endofday(ago(1d)),
      StartOfLastWeek  = startofweek(ago(7d))
      EndOfLastWeek    = endofweek(ago(7d)),
      StartOfLastYear  = startofyear(ago(365d)),
      EndOfLastYear    = endofyear(ago(365d))
```

## Tricky end of last month calculations

- Essentially you go to the start of this month then subtract a day.

```KQL
print RightNow = now(),
      StartOfMonthNow = startofmonth(now),
      StartOfMonthNowMinusOneDay = startofmonth(now()) - 1d,
      StartOfLastMonth = startofmonth((startofmonth(now()) - 1d)),
      EndOfLastMonth = endofmonth((startofmonth(now()) - 1d))
```

## Using tricky last month in a query

```KQL
table_name
| extend StartOfLastMonth = startofmonth((startofmonth(now()) - 1d)),
         EndOfLastMonth = endofmonth((startofmonth(now()) - 1d))
| where TimeColumnName1 between (StartOfLastMonth .. EndOfLastMonth)
| project TimeColumnName1,
          StartOfLastMonth,
          EndOfLastMonth,
          ColumnName1,
          ColumnName2
```

## Compact tricky last month in a query (Does not show Start and End of Month)

```KQL
table_name
| where TimeColumnName1 between (startofmonth((startofmonth(now()) - 1d)) .. endofmonth((startofmonth(now()) - 1d)))
| project TimeColumnName1,
          StartOfLastMonth,
          EndOfLastMonth,
          ColumnName1,
          ColumnName2
```

## Between values/numbers

```KQL
table_name
| where TimeColumnName1 = "string1"
| where ColumnName1 between (20.0 .. 60.0)
| project TimeColumnName1,
          ColumnName2,
          ColumnName1
```

## Not between

``KQL
table_name
| where TimeColumnName1 = "string1"
| where ColumnName1 !between (20.0 .. 60.0)
| project TimeColumnName1,
          ColumnName2,
          ColumnName1
```
