---
layout: home
title: Extract
---

- Similar to split, but instead of separating a string based on a character, extract gets data from a string based on a regular expression.

Data return integer values

> - 0 \- the entire string that matches what's in quotes
> - 1 \-  match the regular expression, but only get the data that is found in the parenthesis.

## Basics

```KQL
table_name
| where ColumnName1 == "String1" and ColumnName2 matches regex "[A-Z]:"
| project ColumnName3,
          ColumnName4,
          ColumnName2,
          RegexColumnName2 = extract("[A-Z]:", 0, ColumnName2)
```

## Return part of the text

```KQL
table_name
| where ColumnName1 == "String1"
| project ColumnName3,
          ColumnName4,
          ColumnName2,
          RegexColumnName2 = extract("([A-Z]):", 1, ColumnName2)
```

## Return more than 1 character

```KQL
table_name
| distinct ColumnName1
| project ColumnName1,
          RegexColumnName1 = extract("([A-Z]{2,4}):", 1, ColumnName1)
```
