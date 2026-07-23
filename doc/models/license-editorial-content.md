
# License Editorial Content

Individual editorial content to license

## Structure

`LicenseEditorialContent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `EditorialId` | `string` | Required | Editorial ID |
| `License` | `string` | Required | License agreement to use for licensing |
| `Metadata` | `*interface{}` | Optional | Additional information for license requests for enterprise accounts and API subscriptions, 4 fields maximum; which fields are required is set by the account holder |
| `Size` | [`*models.SizeEnum`](../../doc/models/size-enum.md) | Optional | Asset size to download<br><br>**Default**: `"original"` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseEditorialContent := models.LicenseEditorialContent{
        EditorialId:          "10687730b",
        License:              "premier_editorial_comp",
        Metadata:             models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
        Size:                 models.ToPointer(models.SizeEnum_ORIGINAL),
    }

}
```

