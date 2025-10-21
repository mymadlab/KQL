---
layout: home
title: Top
---

- First number of rows ranked by a column

## Basic

```KQL
table_name
| top 20 by ColumnName1 desc
```

## With a conditional where

```KQL
table_name
| where ColumnName1 >= ago(10m)
| top 5 by ColumnName2 asc
```
