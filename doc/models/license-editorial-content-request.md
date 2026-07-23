
# License Editorial Content Request

License editorial content request

## Structure

`LicenseEditorialContentRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Country` | [`models.ISOCountryCode`](../../doc/models/containers/iso-country-code.md) | Required | A valid ISO 3166-1 Alpha-2 or ISO 3166-1 Alpha-3 code. |
| `Editorial` | [`[]models.LicenseEditorialContent`](../../doc/models/license-editorial-content.md) | Required | Editorial content to license |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseEditorialContentRequest := models.LicenseEditorialContentRequest{
        Country:              models.ISOCountryCodeContainer.FromISOCountryCode(models.ISOCountryCodeEnum_USA),
        Editorial:            []models.LicenseEditorialContent{
            models.LicenseEditorialContent{
                EditorialId:          "10687730b",
                License:              "premier_editorial_comp",
                Metadata:             models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
                Size:                 models.ToPointer(models.SizeEnum_ORIGINAL),
            },
        },
    }

}
```

