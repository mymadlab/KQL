# Strcat

- String concatenation
- Converts numeric columns to string

## Combining columns/fields

```KQL
table_name
| extend CombinedColumnName1 = strcat(ColumnName1, " - ", ColumnName2, "-", "ColumnName3)
| Project ColumnName4,
          CombinedColumnName1,
          ColumnName1,
          ColumnName2,
          ColumnName3
```

## Get month names with strcar, case, and datetime_part

```KQL
table_name
| where ColumnName1 == "string1"
| where TimeColumnName1 between (ago(365) .. now())
| extend MonthNumber = datetime_part("month", TimeColumnName1),
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
| extend DateStr = strcat(MonthName, " ",
                          datetime_part("day", TimeColumnName1), ", ",
                          datetime_part("year", TimeColumnName1)
                         )
| project TimeColumnName1,
          MonthName,
          DateStr,
          NewStrColumnName1 = strcat("This is a string", ColumnName2),
          ColumnName3,
          ColumnName4
```

