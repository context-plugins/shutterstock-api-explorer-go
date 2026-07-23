
# Instruments

Instruments

## Structure

`Instruments`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*string` | Optional | The string id of the instrument |
| `Name` | `*string` | Optional | The string name of the instrument |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    instruments := models.Instruments{
        Id:                   models.ToPointer("bright_roomy_kit"),
        Name:                 models.ToPointer("Bright Roomy Kit"),
    }

}
```

