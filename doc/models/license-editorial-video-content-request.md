
# License Editorial Video Content Request

License editorial video content request

## Structure

`LicenseEditorialVideoContentRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Country` | [`models.ISOCountryCode`](../../doc/models/containers/iso-country-code.md) | Required | A valid ISO 3166-1 Alpha-2 or ISO 3166-1 Alpha-3 code. |
| `Editorial` | [`[]models.LicenseEditorialVideoContent`](../../doc/models/license-editorial-video-content.md) | Required | Editorial content to license |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseEditorialVideoContentRequest := models.LicenseEditorialVideoContentRequest{
        Country:              models.ISOCountryCodeContainer.FromISOCountryCode(models.ISOCountryCodeEnum_USA),
        Editorial:            []models.LicenseEditorialVideoContent{
            models.LicenseEditorialVideoContent{
                EditorialId:          "10679854a",
                License:              models.License2Enum_PREMIEREDITORIALVIDEODIGITALONLY,
                Metadata:             models.ToPointer(interface{}("[purchase_order, 12345]")),
                Size:                 models.ToPointer(models.Size1Enum_ORIGINAL),
            },
        },
    }

}
```

