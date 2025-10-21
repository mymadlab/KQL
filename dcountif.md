---
layout: home
title: Dcountif
---

- Same as [Dcount](dcount.md), however the seconde parameter is an expression that filters the data/rows.
- Good for large sets of data.
- Trades accuracy for speed.
- Results may vary between runs.
- You can optionally pass an accuracy level as the third parameter. Level 1 is the default.

| Accuracy level | Error % | Entry Count |
| :------------: | :-----: | :---------: |
|        0       |   1.0   |    2^12     |
|        1       |   0.8   |    2^14     |
|        2       |   0.4   |    2^16     |
|        3       |   0.28  |    2^17     |
|        4       |   0.2   |    2^18     |

## Example

```KQL
table_name
| where TimeColumnName1 >= ago(90d)
| summarize ColumnCount3 = dcountif(ColumnName3,
                                    ColumnName2 == "string1") by ColumnName2
| Sort by ColumnName2
```
