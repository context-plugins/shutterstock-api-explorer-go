
# Bands

A band that can be used to generate music

## Structure

`Bands`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*string` | Optional | The ID of the band |
| `Name` | `*string` | Optional | The name of the band |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    bands := models.Bands{
        Id:                   models.ToPointer("1234567"),
        Name:                 models.ToPointer("The Happy Tunes Band"),
    }

}
```

