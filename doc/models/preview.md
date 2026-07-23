
# Preview

Preview information

## Structure

`Preview`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ContentType` | [`*models.ContentTypeEnum`](../../doc/models/content-type-enum.md) | Optional | Content type of the preview, currently audio/mp3 |
| `Url` | `*string` | Optional | Url of the instrument's preview file |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    preview := models.Preview{
        ContentType:          models.ToPointer(models.ContentTypeEnum_ENUMAUDIOMP3),
        Url:                  models.ToPointer("https://public-cdn.ampermusic.com/instruments/previews/roomy_kit_v1.mp3"),
    }

}
```

