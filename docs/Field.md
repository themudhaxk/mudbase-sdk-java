

# Field

Collection field definition (name, type, required, unique, default, validation).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  |
|**type** | [**TypeEnum**](#TypeEnum) |  |  |
|**required** | **Boolean** |  |  [optional] |
|**unique** | **Boolean** |  |  [optional] |
|**_default** | [**FieldDefault**](FieldDefault.md) |  |  [optional] |
|**validation** | **Object** |  |  [optional] |
|**ui** | **Object** |  |  [optional] |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| STRING | &quot;string&quot; |
| NUMBER | &quot;number&quot; |
| BOOLEAN | &quot;boolean&quot; |
| DATE | &quot;date&quot; |
| DATETIME | &quot;datetime&quot; |
| EMAIL | &quot;email&quot; |
| URL | &quot;url&quot; |
| TEXT | &quot;text&quot; |
| ARRAY | &quot;array&quot; |
| OBJECT | &quot;object&quot; |
| REFERENCE | &quot;reference&quot; |
| FILE | &quot;file&quot; |
| ENUM | &quot;enum&quot; |
| JSON | &quot;json&quot; |



