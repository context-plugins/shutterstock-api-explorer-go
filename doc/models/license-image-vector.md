
# License Image Vector

Data required to license an image

## Structure

`LicenseImageVector`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AuthCookie` | [`*models.Cookie`](../../doc/models/cookie.md) | Optional | Cookie object |
| `EditorialAcknowledgement` | `*bool` | Optional | Set to true to acknowledge the editorial agreement |
| `Format` | [`*models.Format1Enum`](../../doc/models/format-1-enum.md) | Optional | (Deprecated) Image format to download<br><br>**Default**: `"eps"` |
| `ImageId` | `string` | Required | Image ID |
| `Metadata` | `*interface{}` | Optional | Additional information for license requests for enterprise accounts and API subscriptions, 4 fields maximum; which fields are required is set by the account holder |
| `Price` | `*float64` | Optional | For revenue-sharing transactions, the final cost to the end customer as a floating-point number in the transaction currency, such as 12.34 |
| `SearchId` | `*string` | Optional | ID of the search that led to this licensing transaction |
| `ShowModal` | `*bool` | Optional | (Deprecated) |
| `Size` | [`*models.Size3Enum`](../../doc/models/size-3-enum.md) | Optional | Image size to download |
| `SubscriptionId` | `*string` | Optional | ID of the subscription to use for the download. |
| `VerificationCode` | `*string` | Optional | (Deprecated) |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseImageVector := models.LicenseImageVector{
        AuthCookie:               nil,
        EditorialAcknowledgement: models.ToPointer(true),
        Format:                   models.ToPointer(models.Format1Enum_EPS),
        ImageId:                  "123456789",
        Metadata:                 models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
        Price:                    models.ToPointer(float64(12.34)),
        ShowModal:                models.ToPointer(true),
        Size:                     models.ToPointer(models.Size3Enum_VECTOR),
        SubscriptionId:           models.ToPointer("s12345678"),
    }

}
```

