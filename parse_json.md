# Parse_json

- Reads JSON from a record and access specific data

## Basic

```KQL
table_name
| where ColumnName1 == "string1"
| project TimeColumnName1,
          ColumnName2,
					JSONColumnName3
| extend JsonPropertiesColumnName3 = parse_json(JSONColumnName3)
| project TimeColumnName1,
          ColumnName2,
					JSONColumnName3
					JsonPropertiesColumnName3["key1"]
					JsonPropertiesColumnName3["key2"]
```

## Rename columns

```KQL
table_name
| where ColumnName1 == "string1"
| project TimeColumnName1,
          ColumnName2,
					JSONColumnName3
| extend JsonPropertiesColumnName3 = parse_json(JSONColumnName3)
| project TimeColumnName1,
          ColumnName2,
					JSONColumnName3
					Key1ColumnName3 = JsonPropertiesColumnName3["key/1"]
					Key2ColumnName3 = JsonPropertiesColumnName3["key/2"]
```

## Reference using property name (no special charters)

```KQL
table_name
| where ColumnName1 == "string1"
| project TimeColumnName1,
          ColumnName2,
					JSONColumnName3
| extend JsonPropertiesColumnName3 = parse_json(JSONColumnName3)
| project TimeColumnName1,
          ColumnName2,
					JSONColumnName3
					Key1ColumnName3 = JsonPropertiesColumnName3["key/1"]
					Key2ColumnName3 = JsonPropertiesColumnName3["key/2"]
					Key3ColumnName3 = JsonPropertiesColumnName3.key3 // Only works if no special characters are in the key name
```