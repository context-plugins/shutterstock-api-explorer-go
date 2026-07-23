
# License Image Result

The response to a licensing request for an image

## Structure

`LicenseImageResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AllotmentCharge` | `*int` | Optional | Number of credits that this licensing event used |
| `Download` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `Error` | `*string` | Optional | Error message, appears only if there was an error |
| `ImageId` | `string` | Required | Image ID that was licensed |
| `LicenseId` | `*string` | Optional | ID of the license event |
| `Price` | [`*models.Price`](../../doc/models/price.md) | Optional | Price |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseImageResult := models.LicenseImageResult{
        AllotmentCharge:      models.ToPointer(1),
        Download:             models.ToPointer(models.Url{
            Url:                  "https://download.shutterstock.com/gatekeeper/[random-characters]/shutterstock_59656357.jpg",
        }),
        Error:                models.ToPointer("error6"),
        ImageId:              "59656357",
        LicenseId:            models.ToPointer("license_id8"),
        Price:                models.ToPointer(models.Price{
            LocalAmount:          models.ToPointer(float64(12.34)),
            LocalCurrency:        models.ToPointer("EUR"),
        }),
    }

}
```

