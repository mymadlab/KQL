# Iif

- If then operator

## Basic

```KQL
table_name
| where ColumnName1 == "string1"
| extend NewColumnName1 = iif(ColumName2 > 50,
                              "True text",
                              "False text"
                             )
| project ColumnName3,
          ColumnName1,
          ColumnName2
```

## Compact version

```KQL
table_name
| where ColumnName1 == "string1"
| project ColumnName3,
          ColumnName1,
          ColumnName2,
          NewColumnName1 = iif(ColumName2 < 70, "True text", "False text")
```

## With Dates

```KQL
table_name
| where ColumnName1 == "string1 and ColumnName2 > 0
| where TimeColumnName1 between(ago(1h) .. now())
| extend RightNow = now()
| extend AdjustedFactor = iif(TimeColumnName1 between((RightNow - 5m) .. RightNow),
                              "Double Weight",
                              "Half Weight"
                             ),
         AdjustedValue = iif(TimeColumnName1 between((RightNow - 5m) .. RightNow),
                             ColumnName2 * 2,
                             ColumnName2 / 2
                            )
| project TimeColumnName1,
          RightNow,
          AdjustedFactor,
          ColumnName2,
          AdjustedValue,
          ColumnName3,
          ColumnName4
| sort by AdjustedFactor,
          TimeColumnName1
```

## More efficient dates

```KQL
table_name
| where ColumnName1 == "string1 and ColumnName2 > 0
| where TimeColumnName1 between(ago(1h) .. now())
| extend RightNow = now()
| IsCurrentValue = (TimeColumnName1 between (RightNow - 5m .. RightNow)) // Returns boolean value
| extend AdjustedFactor = iif(IsCurrentValue == true, "Double Weight", "Half Weight"),
         AdjustedValue = iif(IsCurrentValue, ColumnName2 * 2, ColumnName2 / 2)
| project TimeColumnName1,
          RightNow,
          IsCurrentValue,
          AdjustedFactor,
          ColumnName2,
          AdjustedValue,
          ColumnName3,
          ColumnName4
| sort by AdjustedFactor,
          TimeColumnName1
```
