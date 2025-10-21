---
layout: home
title: IsEmpty / IsNull
---

- Allows you to test if for data that is empty or missing.
- Missing strings are **EMPTY**
- Missing numbers are **NULL**

## IsNull (Numeric)

### IsNull basic

```KQL
table_name
| where isnull(NumberColumn1)
| count
```

### Using isnull to supply missing data

```KQL
table_name
| extend NewColumnName1 = iif(isnull(NumberColumn1),
                              "It's a null value",
                              tostring(NumberColumn1) // Must convert to string so all out comes are the same type
                             )
| project ColumnName1,
          NumberColumn1,
          NewColumnName1,
          ColumnName2
```

## IsEmpty (Strings)

### IsEmpty basic

```KQL
table_name
| where isempty(StringColumnName1)
| count
```

### Using isempty to supply missing data

```KQL
table_name
| where TimeColumnName1 >= ago(1h)
| extend NewColumnName1 = iif(isnull(StringColumnName1),
                              "It's a empty value,
                              StringColumnName1
                             )
| project TimeColumnName1,
          StringColumnName1,
          NewColumnName1,
```