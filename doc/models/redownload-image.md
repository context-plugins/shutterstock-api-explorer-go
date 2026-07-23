
# Redownload Image

Data required to redownload an image

## Structure

`RedownloadImage`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AuthCookie` | [`*models.Cookie`](../../doc/models/cookie.md) | Optional | Cookie object |
| `ShowModal` | `*bool` | Optional | (Deprecated) |
| `Size` | [`*models.Size6Enum`](../../doc/models/size-6-enum.md) | Optional | Size of the image |
| `VerificationCode` | `*string` | Optional | (Deprecated) |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    redownloadImage := models.RedownloadImage{
        AuthCookie:           nil,
        ShowModal:            models.ToPointer(false),
        Size:                 models.ToPointer(models.Size6Enum_SMALL),
        VerificationCode:     models.ToPointer("verification_code4"),
    }

}
```

