
# License Editorial Video Content

Individual editorial video content to license

## Structure

`LicenseEditorialVideoContent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `EditorialId` | `string` | Required | Editorial ID |
| `License` | [`models.License2Enum`](../../doc/models/license-2-enum.md) | Required | License agreement to use for licensing |
| `Metadata` | `*interface{}` | Optional | Additional information for license requests for enterprise accounts and API subscriptions, 4 fields maximum; which fields are required is set by the account holder |
| `Size` | [`*models.Size1Enum`](../../doc/models/size-1-enum.md) | Optional | Asset size to download<br><br>**Default**: `"original"` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseEditorialVideoContent := models.LicenseEditorialVideoContent{
        EditorialId:          "10679854a",
        License:              models.License2Enum_PREMIEREDITORIALVIDEODIGITALONLY,
        Metadata:             models.ToPointer(interface{}("[purchase_order, 12345]")),
        Size:                 models.ToPointer(models.Size1Enum_ORIGINAL),
    }

}
```

