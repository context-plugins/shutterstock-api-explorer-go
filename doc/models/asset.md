
# Asset

## Structure

`Asset`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*string` | Optional | - |
| `Name` | `*string` | Optional | - |
| `Type` | [`models.Type1Enum`](../../doc/models/type-1-enum.md) | Required | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    asset := models.Asset{
        Id:                   models.ToPointer("id0"),
        Name:                 models.ToPointer("name0"),
        Type:                 models.Type1Enum_IMAGE,
    }

}
```

