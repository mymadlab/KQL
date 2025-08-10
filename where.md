# Where

- Condition based search

## Search from from something created in the last 1 hour

```KQL
table_name
| where ColumnName1 >= ago(1h)
```

## Using and/or

### and
```KQL
table_name
| where ColumnName1 >= ago(1h)
  and ColumnName2 == "string1"
```

### or

```KQL
table_name
| where ColumnName1 >= ago(1h)
  and (
    ColumnName2 == "string1"
    or
    ColumnName2 == "string2"
  )
```

### Stacking wheres equal and

```KQL
table_name
| where ColumnName1 >= ago(1h)
| where (
    ColumnName2 == "string1"
    or
    ColumnName2 == "string2"
  )
```

## Simulating search with where

```KQL
table_name
| where * has "string1"
```

## Starts with

```KQL
table_name
| where * startswith "string1"
```

## Ends with

```KQL
table_name
| where * endswith "string1"
```

## Regex

```KQL
table_name
| where ColumnName1 matches regex "[A-Z][a-z][0-9]"
```
