
# License SFX Result

The response to a licensing request for an sound effects

## Structure

`LicenseSFXResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AllotmentCharge` | `*int` | Optional | Number of credits that this licensing event used |
| `Download` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `Error` | `*string` | Optional | Error message, appears only if there was an error |
| `LicenseId` | `*string` | Optional | ID of the license event |
| `SfxId` | `string` | Required | Sound effects ID that was licensed |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseSFXResult := models.LicenseSFXResult{
        AllotmentCharge:      models.ToPointer(1),
        Download:             models.ToPointer(models.Url{
            Url:                  "https://download.shutterstock.com/gatekeeper/[random-characters]/shutterstock_59656357.wav",
        }),
        Error:                models.ToPointer("error8"),
        LicenseId:            models.ToPointer("license_id0"),
        SfxId:                "59656357",
    }

}
```

