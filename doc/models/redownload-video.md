
# Redownload Video

Data required to redownload a video

## Structure

`RedownloadVideo`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AuthCookie` | [`*models.Cookie`](../../doc/models/cookie.md) | Optional | Cookie object |
| `ShowModal` | `*bool` | Optional | (Deprecated) |
| `Size` | [`*models.Size7Enum`](../../doc/models/size-7-enum.md) | Optional | Size of the video |
| `VerificationCode` | `*string` | Optional | (Deprecated) |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    redownloadVideo := models.RedownloadVideo{
        AuthCookie:           nil,
        ShowModal:            models.ToPointer(false),
        Size:                 models.ToPointer(models.Size7Enum_WEB),
        VerificationCode:     models.ToPointer("verification_code0"),
    }

}
```

