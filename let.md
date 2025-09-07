# Let

- Sets variables that be referenced in the query.
- Can be a constant, calculation, or even a function.

## Referencing a constant

```KQL
let minVar1 = 300;
let strVar2 = "string2";
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3
| where ColumnName2 == strVar2,
        ColumnName3 <= minVar1
```

## Calculated value

```KQL
let dateVar1 = ago(12h);
table_name
| project ColumnName1,
          ColumnName2,
          ColumnName3,
          ColumnName4
| where ColumnName2 >= dateVar1
```

## Holding a data set

```KQL
let nameVar1 = "Name1";
let SumVar2 = table_name1
  | project ColumnName1,
            ColumnName2,
            ColumnName3,
            ColumnName4,
            ColumnName5,
            ColumnName6,
            ColumnName7,
            ColumnName8,
            ColumnName9;
let UpDtVar3 = table_name2
  | project ColumnName1,
            ColumnName2,
            ColumnName3,
            ColumnName4,
            ColumnName5,
            ColumnName6,
            ColumnName7,
            ColumnName9,
            ColumnName10;
union withsource = "String2"
      SumVar2,
			UpDtVar3
```

## Defining a function

```KQL
let diffDays = (date1: datetime, date2: datetime=datetime(2018-01-01))
               {(date1-date2)/1d};
print difDays(now(), todatetime("2018-05-01))
```