# Top-nested

- Performs hierarchical aggregation and value selection.
- Supports multiple types of aggregations sum(), count(), max(), min(), dcount(), avg(), percentile(), precentilew(), or any algebraic combination of them.

## Basic

```KQL
table_name
| top-nested 3 of ColumnName1 by NewColumnName1 = count(),
  top-nested 3 of ColumnName2 by NewColumnName2 = count()
| sort by ColumnName1 asc,
          ColumnName2 asc
```

## With others to count the left overs/others

```KQL
table_name
| top-nested 3 of ColumnName1 with others = "ExtrasColumnName1 by NewColumnName1 = count(),
  top-nested 3 of ColumnName2 by NewColumnName2 = count()
| sort by ColumnName1 asc,
          ColumnName2 asc
```

## Can use it at all levels.

```KQL
table_name
| top-nested 3 of ColumnName1 with others = "ExtrasColumnName1" by NewColumnName1 = count(),
  top-nested 3 of ColumnName2 with others = "ExtrasColumnName2" by NewColumnName2 = count()
| sort by ColumnName1 asc,
          ColumnName2 asc
```
