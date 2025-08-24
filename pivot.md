# Pivot

- A plugin that rotates the table by turning the unique values from one column in the table into mutliple columns in the output table.
- Performs aggregations on any remaining column values that will appear in the final output

## Basic

```KQL
table_name
| project ColumnName1, ColumnName2
| evaluate pivot(ColumName)
| sort by ColumName1 asc
```

