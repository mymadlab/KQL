# Makeset / Makelist

- Makeset creates an array of json objects by flattening a hierarchy. Remove multiple values
- Makelist same as makeset, but keeps duplicate values.
- By default they only return 128 items

## Basic example

```KQL
table_name
| summarize Counters = makeset(ColumnName1) by ColumnName2

## Getting a list of something

```KQL
table_name
| where ColumnName1 == "string1"
    and ColumnName2 <= 50
| summarize ColumnName3 = makeset(ColumnName3)
```

## Makelist (duplicate values)

```KQL
table_name
| where ColumnName1 == "string1"
    and ColumnName2 <= 50
| summarize ColumnName3 = makelist(ColumnName3)
```

## Specifying a max return works on both makeset and makelist

```KQL
table_name
| where ColumnName1 == "string1"
    and ColumnName2 <= 50
| summarize ColumnName3 = makelist(ColumnName3, 256)
```