---
layout: home
title: Max/Min
---

- Basic Min and Max aggregation operators similar to arg_max and arg_min, however minus the extra columns.

## Max

```KQL
table_name
| where ColumnName1 == "string1"
| summarize max(ColumnName2)
```

## Min

```KQL
table_name
| where ColumnName1 == "string1"
| summarize min(ColumnName2)
```
