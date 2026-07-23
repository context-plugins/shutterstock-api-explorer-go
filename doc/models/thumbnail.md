
# Thumbnail

Image thumbnail information

## Structure

`Thumbnail`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Height` | `int` | Required | Height in pixels of the image thumbnail |
| `Url` | `string` | Required | Direct URL to the image |
| `Width` | `int` | Required | Width in pixels of the image thumbnail |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    thumbnail := models.Thumbnail{
        Height:               100,
        Url:                  "https://thumb7.shutterstock.com/thumb_large/250738318/1572478477/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
        Width:                150,
    }

}
```

