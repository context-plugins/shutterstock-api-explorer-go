
# License Video Request

List of videos to license

## Structure

`LicenseVideoRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Videos` | [`[]models.LicenseVideo`](../../doc/models/license-video.md) | Required | Videos to license<br><br>**Constraints**: *Maximum Items*: `50` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseVideoRequest := models.LicenseVideoRequest{
        Videos:               []models.LicenseVideo{
            models.LicenseVideo{
                AuthCookie:               nil,
                EditorialAcknowledgement: models.ToPointer(false),
                Metadata:                 models.ToPointer(interface{}("[key1, val1][key2, val2]")),
                Price:                    models.ToPointer(float64(63.12)),
                SearchId:                 models.ToPointer("search_id6"),
                Size:                     models.ToPointer(models.Size5Enum_HD),
                SubscriptionId:           models.ToPointer("s12345678"),
                VideoId:                  "2140697",
            },
        },
    }

}
```

