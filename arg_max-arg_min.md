---
layout: home
title: Arg_max / Arg_min
---

- Get the max/min values in one column with another column and then display other columns

## Display all columns

```KQL
table_name
| summarize arg_max(ColumnName1, *) by ColumnName2 // * retrieves all the columns
| sort by ColumnName2 asc
```

## Specify specific columns

```KQL
table_name
| summarize arg_max(ColumnName1, ColumnName2, ColumnName3) by ColumnName4
| sort by ColumnName4 asc
```

## Example using min and using project to get only certain columns

```KQL
table_name
| project ColumnName2, ColumnName1
| summarize arg_min(ColumnName1, *) by ColumnName2 // * retrieves all the columns
| sort by ColumnName2 asc
```
