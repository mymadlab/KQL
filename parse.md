# Parse

- Like split, however it divides by one or text strings.
- If the string stored in the column is inconsistent then multiple queries may be needed.

## Parse Basics

```KQL
table_name
| parse ColumnName1 with "string1" ParsedColumnName1
| project TimeColumnName1,
          ColumnName1,
					ParsedColumnName1
```

Will find string1 and then remove it and everything before it. If parsed does not find a match the output (ParsedColumnName1) is empty.  Good idea to use an isempty check here.

## Multiple Column Parse

```KQL
table_name
| where ColumnName1 == "string1" and ColumnName2 == "string2"
| parse ColumnName1 with "GET" ParsedColumnName1
| project TimeColumnName1,
          ColumnName1,
					ColumnName2,
					ColumnName3
| parse ColumnName3 with "prefixstring2" ParsedColumnName3a "midstring3" ParsedColumnName3b "postfixstring4" ParsedColumnName3c
```

- Will locate and remove prefixstring2 and everything before, store everything up to midstring3 in ParsedColumnName3a.
- Everything after midstring3 up to postfixstring4 is stored in ParsedColumnName3b 
- Anything after postfixstring4 is stored in ParsedColumnName3c
