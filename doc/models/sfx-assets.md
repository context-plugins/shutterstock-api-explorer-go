
# SFX Assets

Files that are available as part of an sound effect asset

## Structure

`SFXAssets`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `PreviewMp3` | [`*models.SFXAssetDetails`](../../doc/models/sfx-asset-details.md) | Optional | Information about a file that is part of an sound effect asset |
| `Waveform` | [`*models.SFXAssetDetails`](../../doc/models/sfx-asset-details.md) | Optional | Information about a file that is part of an sound effect asset |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    sFXAssets := models.SFXAssets{
        PreviewMp3:           models.ToPointer(models.SFXAssetDetails{
            FileSize:             models.ToPointer(123),
            Url:                  models.ToPointer("https://cdn.shutterstock.com/shutterstock/sfx/11222/preview_ecom_ster/hand-throw-catch-cellphone.mp3"),
        }),
        Waveform:             models.ToPointer(models.SFXAssetDetails{
            FileSize:             models.ToPointer(123),
            Url:                  models.ToPointer("https://cdn.shutterstock.com/shutterstock/sfx/11222/preview_ecom_ster/hand-throw-catch-cellphone.mp3"),
        }),
    }

}
```

