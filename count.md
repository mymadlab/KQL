# Count

- Counts the number of rows

## Count the whole table

```KQL
table_name
| count
```

## Count based off of where

```KQL
table_name
| where ColumnName1 >= ago(1h)
  and ColumnName2 == "string1"
  and ColumnName3 > 0
| count
```
