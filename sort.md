---
layout: home
title: Sort
---

- Orders output based off of one or more columns
- Order is descending (desc) by default. You can specify ascending (asc)
- **Alias:** order

## Sort all columns in ascending order

```KQL
table_name
| where ColumnName1 == "string1"
| where ColumnName2 > ago(3m)
| project ColumnName1,
          ColumnName2,
          ColumnName3,
          ColumnName4
| sort by ColumnName1,
          ColumnName4,
          ColumnName2
```

## Each column different sort order

```KQL
table_name
| where ColumnName1 == "string1"
| where ColumnName2 > ago(3m)
| project ColumnName1,
          ColumnName2,
          ColumnName3,
          ColumnName4
| sort by ColumnName1 asc,
          ColumnName4 asc,
          ColumnName2 desc
```
