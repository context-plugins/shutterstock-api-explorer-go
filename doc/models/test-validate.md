
# Test Validate

Validation results

## Structure

`TestValidate`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Header` | [`*models.TestValidateHeader`](../../doc/models/test-validate-header.md) | Optional | Validation results |
| `Query` | [`*models.TestValidateQuery`](../../doc/models/test-validate-query.md) | Optional | Validation results |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    testValidate := models.TestValidate{
        Header:               models.ToPointer(models.TestValidateHeader{
            UserAgent:            models.ToPointer("Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36"),
        }),
        Query:                models.ToPointer(models.TestValidateQuery{
            Id:                   123456,
            Tag:                  []string{
                "Test string",
            },
        }),
    }

}
```

