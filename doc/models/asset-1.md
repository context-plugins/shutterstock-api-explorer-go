
# Asset 1

## Structure

`Asset1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*string` | Optional | - |
| `Type` | `string` | Required | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    asset1 := models.Asset1{
        Id:                   models.ToPointer("id0"),
        Type:                 "type0",
    }

}
```

