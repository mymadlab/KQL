# Format_datetime

- Outputs datetime types based on the defined format returning a string.

## Syntax

### Date formatting

```
d    - Day, 1 to 31
dd   - Day, 01 to 31
M    - Month, 1 to 12
MM   - Month, 01 to 12
y    - Year, 0 to 9999
yy   - Year, 00 to 9999
yyyy - Year, 0000 to 9999
```

### Time formatting

```
h  - 12 hour, 1 to 12
hh - 12 hour, 01 to 12
H  - 24 hour, 0 to 23
HH - 24 hour, 00 to 23
m  - Minute, 0 to 59
mm - Minute, 00 to 59
s  - second, 0 to 59
ss - second, 00 to 59
tt - am/pm
```

>f/F displays sub seconds. The number of them indicates the precision down to millionth of a second. A lowercase f will always display a 0, where uppercase F will display only if there is a subsecond value.

### Allowed Separators

> / \- : , . _ [ ] or a space

## Displaying various formats

```KQL
print D1 = format_datetime(TimeColumn1, "y-M-d")
			D2 = format_datetime(TimeColumn1, "yyyy-MM-dd")
			D3 = format_datetime(TimeColumn1, "MM/dd/yyyy")
			T1 = format_datetime(TimeColumn1, "MM/dd/yyyy hh:mm:ss tt")
			T2 = format_datetime(TimeColumn1, "MM/dd/yyyy HH:mm:ss")
			T3 = format_datetime(TimeColumn1, "MM/dd/yyyy HH:mm:ss.ffff")
```

## Format_datetime basics

```KQL
table_name
| where TimeColumn1 >= ago(60d)
| project TimeColumn1,
          D1 = format_datetime(TimeColumn1, "y-M-d")
					D2 = format_datetime(TimeColumn1, "yyyy-MM-dd")
					D3 = format_datetime(TimeColumn1, "MM/dd/yyyy")
					T1 = format_datetime(TimeColumn1, "MM/dd/yyyy hh:mm:ss tt")
					T2 = format_datetime(TimeColumn1, "MM/dd/yyyy HH:mm:ss")
					T3 = format_datetime(TimeColumn1, "MM/dd/yyyy HH:mm:ss.ffff")
					ColumnName1,
					ColumnName2
```

## Separating Date and time

```KQL
Table_name
| project TimeColumn1,
          TheDate = format_datetime(TimeColumn1, "yyyy-MM-dd"),
          TheTime = format_datetime(TimeColumn1, "hh:mm:ss tt"),
					ColumnName1,
					ColumnName2
```