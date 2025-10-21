---
layout: home
title: Contains and In
---

- Contains searches a string for a sub string
- In takes multiple strings and looks to match one of those strings.

## Variants

### String case sensitivity

The following operators are all case insensitive

> startswith, endswith, has, hasprefix, hassuffix, and contains

Each of them has a case sensitive version where you simply add _cs at the end like so

> startswith_cs, endswith_cs, has_cs, hasprefix_cs, hassuffix_cs, and contains_cs


### Not versions

There are also not versions of these where you simply add ! at the start of each of them.

Case insensitive not

> !startswith, !endswith, !has, !hasprefix, !hassuffix, and !contains

Case sensitive not

> !startswith_cs, !endswith_cs, !has_cs, !hasprefix_cs, !hassuffix_cs, and !contains_cs

## Basic case

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 contains "STRING1"
```

## Basic case sensitive 

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 contains_cs "STRING1"
```

## Basic not case insensitive

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 !contains "STRING1"
```

## Basic not case sensitive

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 !contains_cs "STRING1"
```

## Using in to select from a list of options (Case sensitive)

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 in ("String1", "String2", "String3")
```

## Using in to select from a list of options (Case insensitive)

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 in~ ("string1", "STRING2", "StRing3")
```

## Using not in to select from a list of options (Case sensitive)

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 !in ("String1", "String2", "String3")
```

## Using not in to select from a list of options (Case insensitive)

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 !in~ ("string1", "STRING2", "StRing3")
```
