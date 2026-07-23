
# License Image Request

Image license request data

## Structure

`LicenseImageRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Images` | [`[]models.LicenseImageRequestImages`](../../doc/models/containers/license-image-request-images.md) | Required | This is Array of a container for any-of cases.<br><br>**Constraints**: *Maximum Items*: `50` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseImageRequest := models.LicenseImageRequest{
        Images:               []models.LicenseImageRequestImages{
            models.LicenseImageRequestImagesContainer.FromLicenseImage(models.LicenseImage{
                AuthCookie:               nil,
                CustomDimensions:         nil,
                EditorialAcknowledgement: models.ToPointer(true),
                Format:                   models.ToPointer(models.FormatEnum_JPG),
                ImageId:                  "123456789",
                Metadata:                 models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
                Price:                    models.ToPointer(float64(12.34)),
                ShowModal:                models.ToPointer(true),
                Size:                     models.ToPointer(models.Size2Enum_SMALL),
                SubscriptionId:           models.ToPointer("s12345678"),
            }),
        },
    }

}
```

