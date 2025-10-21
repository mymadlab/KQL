---
layout: home
title: Percentiles
---

- Calculate values that are greater than a percentage for a given sample

## Value of things that are higher than 5%, then 50%, and lastly 90%

```KQL
table_name
| where ColumnName1 == "string1"
| summarize percentiles(ColumnName2, 5, 50, 90) by ColumnName3
```

## Renaming the percentile column names (project-rename)

```KQL
table_name
| where ColumnName1 == "string1"
| summarize percentiles(ColumnName2, 5, 50, 90) by ColumnName3
| project-rename Percent05 = percentile_ColumName2_5,
                 Percent50 = percentile_ColumName2_50,
                 Percent90 = percentile_ColumName2_90,
```

## Better renaming using summarize

```KQL
table_name
| where ColumnName1 == "string1"
| summarize (Percent05, Percent50, Percent90)
            = percentiles(ColumnName2, 5, 50, 90)
            by ColumnName3
```

## Return the values as an array or single column

```KQL
table_name
| summarize percentiles_array(ColumnName2, 5, 50, 90) by ColumnName3
```

## Combine with mv-expand to convert it to individual rows.


```KQL
table_name
| summarize MyColumnName3 = percentiles_array(ColumnName1, 5, 50, 90) by ColumnName2
| mv-expand MyColumnName3
```
