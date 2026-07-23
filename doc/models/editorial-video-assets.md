
# Editorial Video Assets

Asset information, including size and thumbnail URLs

## Structure

`EditorialVideoAssets`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Original` | [`*models.VideoSizeDetails`](../../doc/models/video-size-details.md) | Optional | Video asset information |
| `PreviewMp4` | [`*models.VideoPreviewUrl`](../../doc/models/video-preview-url.md) | Optional | Video preview information |
| `PreviewWebm` | [`*models.VideoPreviewUrl`](../../doc/models/video-preview-url.md) | Optional | Video preview information |
| `ThumbJpg` | [`*models.VideoPreviewUrl`](../../doc/models/video-preview-url.md) | Optional | Video preview information |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    editorialVideoAssets := models.EditorialVideoAssets{
        Original:             models.ToPointer(models.VideoSizeDetails{
            DisplayName:          models.ToPointer("HD"),
            FileSize:             models.ToPointer(82233387),
            Format:               models.ToPointer("avc1"),
            Fps:                  models.ToPointer(float64(30)),
            Height:               models.ToPointer(1080),
            IsLicensable:         models.ToPointer(true),
            Width:                models.ToPointer(1080),
        }),
        PreviewMp4:           models.ToPointer(models.VideoPreviewUrl{
            Url:                  "https://qa.editorial-cdn.shuttercorp.net/wm-preview-mp4/10679854a/M0T7A13aNej2g82bMTI4NjY=/Shutterstock_10679854a.mp4",
        }),
        PreviewWebm:          models.ToPointer(models.VideoPreviewUrl{
            Url:                  "https://qa.editorial-cdn.shuttercorp.net/wm-preview-webm/10679854a/M4T6A63fN2j5g929MTI4NjY=/Shutterstock_10679854a.webm",
        }),
        ThumbJpg:             models.ToPointer(models.VideoPreviewUrl{
            Url:                  "https://qa.editorial-cdn.shuttercorp.net/thumb-1/10679854a/M5TcAf30Ncjcge2eMTI4NjY=/Shutterstock_10679854a.jpg",
        }),
    }

}
```

