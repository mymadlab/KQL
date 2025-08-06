# Distinct

- Find unique value in a column or unique combinations across multiple columns

## Single column

```KQL
table_name
| distinct ColumnName1
| sort by ColumnName1 asc
```

## Unique combinations across multiple columns

```KQL
table_name
| distinct ColumnName1,
           ColumnName2
| sort by ColumnName1,
          ColumnName2
```

## Inclusion with where

```KQL
table_name
| where columnName1 == "string1"
| distinct ColumnName1
| sort by ColumnName1 asc
```
