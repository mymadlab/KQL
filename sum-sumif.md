# Sum/Sumif

- Sum returns a grand total of the indicated column
- Sumif allows for you to filter based on a condition like countif

## Sum

```KQL
table_name
| where ColumnName1 == "string1"
| summarize sum(ColumnName2)
```

## Sumif

```KQL
table_name
| summarize sumif(ColumnName2, ColumnName1 == "string1")
```