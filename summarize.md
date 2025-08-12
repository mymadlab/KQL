# Summarize

- Create aggregations by column names

## Single summarization using the count function

```KQL
table_name
| summarize count() by ColumnName1
```

## Summarization on multiple columns

```KQL
table_name
| summarize count() by ColumnName1, ColumnName2
```

## Renaming the _count column to Counter (or your choice)

```KQL
table_name
| summarize Counter=count()
  by ColumnName1, ColumnName2
```