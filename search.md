# Search Syntax and Notes

- Search will only look in columns that match the type of data being searched for.
- Search like most of KQL is case insensitive

## Search for keyword across all columns

```KQL
table_name
| search "string1"
```

## Case sensitive search

```KQL
table_name
| search kind=case_sensitive "string1"
```

## Multiple table search

```KQL
search in (table1, table2, etc.) "string1"
```

## Exact match in a specific column

```KQL
table_name
| search ColumnName1 == "string1"
```

## Search for sub string

```KQL
table_name
| search "*rin*"
```

## Starts With

```KQL
table_name
| search startswith "string1"
```

## Ends With

```KQL
table_name
| search endswith "string1"
```

## Starts with, any text, and ends with

```KQL
table_name
| search "string1*string2"
```

## Using and/or

```KQL
table_name
| search "string1" and ("Hello" or "World")
```

## Using Regex

```KQL
table_name
| search ColumnName1 matches regex "[A-Z][a-z][0-9]"
```
