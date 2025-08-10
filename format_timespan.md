# Format_timespan

- Formats the amount of time between two dates

## Syntax

There is no 12 hour clock format of **h** (lowercase), as this calculates the elapsed hours not the time of day.

```
d  - Day, number D's indicates how many 0s to use
H  - Hour, 0 to 23 (24 hour clock)
HH - Hour, 00 to 23 (24 hour clock)
m  - Minute, 0 to 59
mm - Minute, 00 to 59
s  - Second, 00 to 59
ss - Second, 00 to 59
f  - Sub-second
F  - Sub-second for non-zero values
```
### Allowed Separators

> / \- : , . _ [ ] or a space

## Format_timespan basics

```KQL
table_name
| where TimeColumnName1 between(ago(7d) .. now())
| extend TimeGen = Now() - TimeColumnName1
| project TimeColumnName1,
          TimeGen,
					TS1 = format_timespan(TimeGen, "dd.HH.:mm:ss"),
					TS2 = format_timespan(TimeGen, "dd HH:mm:ss"),
					TS3 = format_timespan(TimeGen, "d.H:m:s"),
					TS4 = format_timespan(TimeGen, "d H:m:s"),
					ColumnName1,
					ColumnName2
```

## Examples using print

```KQL
print format_timespan(now() - ago(3d), "dd.HH.:mm:ss"),
      format_timespan(now() - ago(3d), "dd HH:mm:ss"),
      format_timespan(now() - ago(3d), "d.H:m:s"),
      format_timespan(now() - ago(3d), "d H:m:s"),
      format_timespan(now() - ago(3d), "d.HH:mm:ss.f"),
      format_timespan(now() - ago(3d), "d HH:mm:ss.F"),
      format_timespan(now() - ago(3d), "dd - HH:mm:ss.ff"),
      format_timespan(now() - ago(3d), "dd - HH:mm:ss.FF"),
      format_timespan(now() - ago(3d), "ddd, HH:mm:ss.fff"),
      format_timespan(now() - ago(3d), "ddd, HH:mm:ss.FFF"),
      format_timespan(now() - ago(3d), "dddd_HH:mm:ss.ffff"),
      format_timespan(now() - ago(3d), "dddd_HH:mm:ss.FFFF"),
      format_timespan(now() - ago(3d), "ddddd HH:mm:ss [fffff]"),
      format_timespan(now() - ago(3d), "ddddd HH:mm:ss [FFFFF]"),
      format_timespan(now() - ago(3d), "dddddd HH:mm:ss.ffffff"),
      format_timespan(now() - ago(3d), "dddddd HH:mm:ss.FFFFFF"),
      format_timespan(now() - ago(3d), "ddddddd / HH:mm:ss.fffffff"),
      format_timespan(now() - ago(3d), "ddddddd / HH:mm:ss.FFFFFFF")
```

## Into Specific columns

```KQL
table_name
| where TimeColumnName1 between(ago(7d) .. now())
| extend TimeGen = endofweek(Now()) - TimeColumnName1
| project TimeColumnName1,
          TimeGen,
					Days       = format_timespan(TimeGen, "dd"),
					Hours      = format_timespan(TimeGen, "HH"),
					Minutes    = format_timespan(TimeGen, "mm"),
					Seconds    = format_timespan(TimeGen, "ss"),
					Subseconds = format_timespan(TimeGen, "ffff"),
					ColumnName1,
					ColumnName2
```

## Creating sentences using format_timespan and strcat

```KQL
table_name
| where TimeColumnName1 between(ago(7d) .. now())
| extend TimeGen = endofweek(Now()) - TimeColumnName1
| project TimeColumnName1,
          TimeGen,
					Sentence = strcat ("Hello it has been ",
					format_timespan(TimeGen, "dd"), " days ",
					format_timespan(TimeGen, "hh"), " hours ",
					format_timespan(TimeGen, "mm"), " minutes, and "
					format_timespan(TimeGen, "ss,ff"), " seconds."
					)
					ColumnName1,
					ColumnName2
```

