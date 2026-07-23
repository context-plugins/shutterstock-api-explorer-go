
# Image 1

## Structure

`Image1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AuthCookie` | [`*models.Cookie`](../../doc/models/cookie.md) | Optional | Cookie object |
| `CustomDimensions` | [`*models.CustomSizeDimensions`](../../doc/models/custom-size-dimensions.md) | Optional | A custom height or a custom width to resize the image to, but not both (experimental) |
| `EditorialAcknowledgement` | `*bool` | Optional | Set to true to acknowledge the editorial agreement |
| `Format` | [`*models.FormatEnum`](../../doc/models/format-enum.md) | Optional | (Deprecated) Image format to download<br><br>**Default**: `"jpg"` |
| `ImageId` | `*string` | Optional | Image ID |
| `Metadata` | `*interface{}` | Optional | Additional information for license requests for enterprise accounts and API subscriptions, 4 fields maximum; which fields are required is set by the account holder |
| `Price` | `*float64` | Optional | For revenue-sharing transactions, the final cost to the end customer as a floating-point number in the transaction currency, such as 12.34 |
| `SearchId` | `*string` | Optional | ID of the search that led to this licensing transaction |
| `ShowModal` | `*bool` | Optional | (Deprecated) |
| `Size` | [`*models.Size2Enum`](../../doc/models/size-2-enum.md) | Optional | Image size to download |
| `SubscriptionId` | `*string` | Optional | ID of the subscription to use for the download. |
| `VerificationCode` | `*string` | Optional | (Deprecated) |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    image1 := models.Image1{
        AuthCookie:               models.ToPointer(models.Cookie{
            Name:                 "The name of the cookie",
            Value:                "The value of the cookie",
        }),
        CustomDimensions:         models.ToPointer(models.CustomSizeDimensions{
            Height:               models.ToPointer(600),
            Width:                models.ToPointer(800),
        }),
        EditorialAcknowledgement: models.ToPointer(false),
        Format:                   models.ToPointer(models.FormatEnum_JPG),
        ImageId:                  models.ToPointer("image_id2"),
        Metadata:                 models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
    }

}
```

