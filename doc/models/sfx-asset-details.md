
# SFX Asset Details

Information about a file that is part of an sound effect asset

## Structure

`SFXAssetDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `FileSize` | `*int` | Optional | File size of the sound effect |
| `Url` | `*string` | Optional | URL the sound effect is available at |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    sFXAssetDetails := models.SFXAssetDetails{
        FileSize:             models.ToPointer(123),
        Url:                  models.ToPointer("https://cdn.shutterstock.com/shutterstock/sfx/11222/preview_ecom_ster/hand-throw-catch-cellphone.mp3"),
    }

}
```

