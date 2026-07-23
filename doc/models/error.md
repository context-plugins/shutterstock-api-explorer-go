
# Error

Error object

## Structure

`Error`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Code` | `*string` | Optional | The error code of this error |
| `Data` | `*string` | Optional | Debugging information about the error |
| `Items` | `[]interface{}` | Optional | A list of items that produced the error |
| `Message` | `string` | Required | Specific details about this error |
| `Path` | `*string` | Optional | Internal code reference to the source of the error |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    mError := models.Error{
        Code:                 models.ToPointer("VALIDATION_INVALID_TYPE"),
        Data:                 models.ToPointer("'10'"),
        Items:                []interface{}{
            interface{}("[key1, val1][key2, val2]"),
        },
        Message:              "Invalid type: string should be integer",
        Path:                 models.ToPointer("$.query.page"),
    }

}
```

