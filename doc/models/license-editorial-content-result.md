
# License Editorial Content Result

The response to a licensing request for editorial content

## Structure

`LicenseEditorialContentResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AllotmentCharge` | `*int` | Optional | For pre-paid plans, how many credits were used for the item license |
| `Download` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `EditorialId` | `string` | Required | Editorial ID |
| `Error` | `*string` | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseEditorialContentResult := models.LicenseEditorialContentResult{
        AllotmentCharge:      models.ToPointer(1),
        Download:             models.ToPointer(models.Url{
            Url:                  "https://s3-eu-west-1.amazonaws.com/api-downloads.rexfeatures.com/[random-characters].jpg?Expires=1524717323",
        }),
        EditorialId:          "69656358",
        Error:                models.ToPointer("error0"),
    }

}
```

