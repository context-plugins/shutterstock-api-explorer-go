
# Test Validate Query

Validation results

## Structure

`TestValidateQuery`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `int` | Required | Integer ID that was passed in the request |
| `Tag` | `[]string` | Optional | List of tags that were passed in the request |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    testValidateQuery := models.TestValidateQuery{
        Id:                   123456,
        Tag:                  []string{
            "string",
        },
    }

}
```

