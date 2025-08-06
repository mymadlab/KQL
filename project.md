# Project

- Select one or more columns
- It is possible to use multiple projects

## Basic return only specific columns

```KQL
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3,
          ColumnName4,
          ColumnName5
```

## Combination with extend (Requires extra column name)

```KQL
table_name
| where ColumnName1 == "string1"
| project ColumnName1,
          ColumnName2,
          ColumnName3,
          ColumnName4,
          ColumnName5
| extend NewColumnName1 = ColumnName2/1000
```

## Combination with extend (No extra column)

```KQL
table_name
| where ColumnName1 == "string1"
| extend NewColumnName1 = ColumnName2/1000
| project ColumnName1,
          ColumnName3,
          ColumnName4,
          ColumnName5,
					NewColumnName1
```

## Project can perform calculations thus eliminating extend

```KQL
table_name
| where ColumnName1 == "string1"
| project ColumnName1,
          ColumnName3,
          ColumnName4,
          ColumnName5,
					NewColumnName1 = ColumnName2/1000
```

## Project Variants

### project-away

- List the columns that you do not want

```KQL
table_name
| where ColumnName1 < ago(1h)
| project-away ColumnName2,
          ColumnName3,
          ColumnName4,
          ColumnName5
```

### project-rename

- Rename columns

```KQL
table_name
| where ColumnName1 == "string1"
| project ColumnName1,
          ColumnName2,
          ColumnName3
|project-rename NewColumnName1 = ColumnName2
```

- With better ordering

```KQL
table_name
| where ColumnName1 == "string1"
|project-rename NewColumnName1 = ColumnName2
| project ColumnName1,
          NewColumnName1,
          ColumnName3
```

### project-keep

- Outputs the same order as configured in the table (ignores your order)

```KQL
table_name
| where ColumnName1 == "string1"
| project-keep ColumnName1,
          ColumnName6,
          ColumnName5,
          ColumnName4,
          ColumnName2
```

- Can use wildcard (*) for column names

```KQL
table_name
| where ColumnName1 == "string1"
| project-keep ColumnName3,
          Other*,
          ColumnName1
```

### project-reorder

- Select order of initial columns then display the rest as the table is ordered
- Does support wildcards (*)

```KQL
table_name
| where ColumnName1 == "string1"
| project-reorder ColumnName1,
          ColumnName6,
          ColumnName5,
          ColumnName4,
          ColumnName2
```

- Wildcard example ordering all in ascending order

```KQL
table_name
| where ColumnName1 == "string1"
| project-reorder * asc
```
