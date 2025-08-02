# Take

- Returns a specified number of random rows
- Useful for testing queries with smaller intake of records to help speed development time
- **limit** is an alias for take

## Return random 10 Rows

```KQL
table_name
| take 10
```

## Adding a where operator

```KQL
table_name
| where ColumnName1 >= ago(1h)
| take 10
```

## Complex

```KQL
table_name
| where ColumnName1 >= ago(1h)
  and ColumnName2 == "string1"
| where ColumName3 > 0
| take 30
```
