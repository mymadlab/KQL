# Extend

- Add/Remove columns with or without calculated values

## Adding one column

```KQL
table_name
| where ColumnName1 == "string1"
| extend NewColumnName1 = ColumnName2 / 1000
```

## Multiple columns

```KQL
table_name
| where ColumnName1 == "string1"
| extend NewColumnName1 = ColumnName2 / 1000,
         NewColumnName2 = ColumnName3 * 1000,
         NewColumnName3 = ColumnName4 
```
