
# License Video

Data required to license a video

## Structure

`LicenseVideo`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AuthCookie` | [`*models.Cookie`](../../doc/models/cookie.md) | Optional | Cookie object |
| `EditorialAcknowledgement` | `*bool` | Optional | Whether or not this item is editorial content |
| `Metadata` | `*interface{}` | Optional | Additional information for license requests for enterprise accounts and API subscriptions, 4 fields maximum; which fields are required is set by the account holder |
| `Price` | `*float64` | Optional | Retail price amount as a floating-point number in the transaction currency, such as 12.34; only for rev-share partners |
| `SearchId` | `*string` | Optional | ID of the search that led to this licensing event |
| `ShowModal` | `*bool` | Optional | (Deprecated) |
| `Size` | [`*models.Size5Enum`](../../doc/models/size-5-enum.md) | Optional | Size of the video being licensed |
| `SubscriptionId` | `*string` | Optional | ID of the subscription used for this license |
| `VideoId` | `string` | Required | ID of the video being licensed |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseVideo := models.LicenseVideo{
        AuthCookie:               nil,
        EditorialAcknowledgement: models.ToPointer(false),
        Metadata:                 models.ToPointer(interface{}("[key1, val1][key2, val2]")),
        Price:                    models.ToPointer(float64(205.28)),
        SearchId:                 models.ToPointer("search_id2"),
        Size:                     models.ToPointer(models.Size5Enum_HD),
        SubscriptionId:           models.ToPointer("s12345678"),
        VideoId:                  "2140697",
    }

}
```

