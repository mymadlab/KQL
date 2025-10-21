---
layout: home
title: Split
---

- Breaks down larger strings into several smaller strings.

## Basic example

```KQL
table_name
| project ColumnName1,
          SplitColumnName1 = split(ColumnName1, "\\"), // \\ is needed to escape a single \
          ColumnName2,
          ColumnName3
```

This can leave an empty spot in the array if ColumName starts with \\\\.  This can be eliminated by doing a parse.  You'll need to escape both \, resulting in four total \\\\\\\\ to equal \\\\.

## Solving the empty spots with parse

```KQL
table_name
| parse ColumnName1 with "\\\\" ParsedColumnName1 // \\\\ is needed to escape a \ resulting in \\ 
| project ColumnName1,
          ParsedColumnName1,
          ParsedSplitColumnName1 = split(ParsedColumnName1, "\\"), // \\ is needed to escape a single \
          ColumnName2,
          ColumnName3
```

## Extracting a specific item from the array

```KQL
table_name
| parse ColumnName1 with "\\\\" ParsedColumnName1
| extend SplitColumn1 = split(ParsedColumnName1, "\\", 0),
         SplitColumn2 = split(ParsedColumnName1, "\\", 1),
         SplitColumn3 = split(ParsedColumnName1, "\\", 2)
| project ColumnName1,
          ParsedColumnName1,
          SplitColumn1,
          SplitColumn2,
          SplitColumn3,
          ColumnName2,
          ColumnName3
```

The SplitColumns will be an array.

## Make the individual item a string instead of an array.

```KQL
table_name
| parse ColumnName1 with "\\\\" ParsedColumnName1
| extend SplitArrayColumn1 = split(ParsedColumnName1, "\\", 0)
| project ColumnName1,
          ParsedColumnName1,
          SplitColumn1 = SplitArrayColumn1[0],
          SplitColumn2 = SplitArrayColumn1[1],
          SplitColumn3 = SplitArrayColumn1[2],
          ColumnName2,
          ColumnName3
```
