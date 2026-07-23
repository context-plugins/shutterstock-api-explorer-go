
# License Video Result

The response to a licensing request for a video

## Structure

`LicenseVideoResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AllotmentCharge` | `*int` | Optional | Number of credits that this licensing event used |
| `Download` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `Error` | `*string` | Optional | Potential error that occurred during licensing |
| `LicenseId` | `*string` | Optional | ID of the license event |
| `Price` | [`*models.Price`](../../doc/models/price.md) | Optional | Price |
| `VideoId` | `string` | Required | ID of the video that was licensed |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseVideoResult := models.LicenseVideoResult{
        AllotmentCharge:      models.ToPointer(1),
        Download:             models.ToPointer(models.Url{
            Url:                  "https://download.shutterstock.com/gatekeeper/[random-characters]/shutterstock_59656357.mp4",
        }),
        Error:                models.ToPointer("error4"),
        LicenseId:            models.ToPointer("license_id6"),
        Price:                models.ToPointer(models.Price{
            LocalAmount:          models.ToPointer(float64(12.34)),
            LocalCurrency:        models.ToPointer("EUR"),
        }),
        VideoId:              "123456789",
    }

}
```

