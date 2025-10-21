---
layout: home
title: Take_any
---

- Randomly selects a row

## Select any random row

```KQL
table_name
| summarize any(*)
```

## Select any random row and return just one column

```KQL
table_name
| summarize any(ColumnName1)
```

## Select any random row and return just multiple columns

```KQL
table_name
| summarize any(ColumnName1, ColumnName2, ColumnName3)
```


## Return a random row for each distinct value

```KQL
table_name
| summarize any(*) by ColumnName1
| sort by ColumnName1 asc
```
