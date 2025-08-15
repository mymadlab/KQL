# Mv-expand

- Expands multi-value dynamic values similar to what makeset or makelist create and converts it to rows

## Basic

```KQL
table_name
| where ColumnName1 == "string1"
    and ColumnName2 >- 50
| summarize MyColumnName3 = makeset(ColumnName3)
| mv-expand MyColumnName3
```

## Converting JSON into individual values

```KQL
table_name
| extend MyProperties=parse_json(ColumnName1)
| mv-expand MyProperties
| project ColumnName2,
          ColumnName3,
					ColumnName4,
					ColumnName5,
					MyProperties
```
