---
layout: home
title: Summarize
---

- Allows you to count rows by column using count(), avg(), etc.

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
| summarize Counter = count()
  by ColumnName1, ColumnName2
```

##  Using average

```KQL
table_name
| where ColumName1 == "string1"
| summarize Counter = count()
            AvgColumnName2 = avg(ColumnName2)
            by ColumnName1
```

## Using bin to summarize into logical groups by day

```KQL
table_name
| summarize Counter = count()
         by ColumnName1
            bin(TImeColumn1, 1d)
```

## Multiple levels

```KQL
table_name
| summarize Counter = count()
         by ColumnName1,
				    bin(TimeColumn1, 1d)
```