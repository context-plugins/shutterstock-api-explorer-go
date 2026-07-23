
# Image Assets

Information about the assets that are part of an image

## Structure

`ImageAssets`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `HugeJpg` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |
| `HugeThumb` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `LargeThumb` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `MediumJpg` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |
| `Preview` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `Preview1000` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `Preview1500` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `SmallJpg` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |
| `SmallThumb` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `SupersizeJpg` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |
| `VectorEps` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    imageAssets := models.ImageAssets{
        HugeJpg:              nil,
        HugeThumb:            models.ToPointer(models.Thumbnail{
            Height:               260,
            Url:                  "https://image.shutterstock.com/image-photo/cropped-image-woman-gardening-260nw-1572478477.jpg",
            Width:                390,
        }),
        LargeThumb:           models.ToPointer(models.Thumbnail{
            Height:               100,
            Url:                  "https://thumb7.shutterstock.com/thumb_large/250738318/1572478477/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
            Width:                150,
        }),
        MediumJpg:            nil,
        Preview:              models.ToPointer(models.Thumbnail{
            Height:               300,
            Url:                  "https://image.shutterstock.com/display_pic_with_logo/250738318/1572478477/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
            Width:                450,
        }),
        Preview1000:          models.ToPointer(models.Thumbnail{
            Height:               667,
            Url:                  "https://ak.picdn.net/shutterstock/photos/1572478477/watermark_1000/1706028c641ea2f443057287c67d9b91/preview_1000-1572478477.jpg",
            Width:                1000,
        }),
        Preview1500:          models.ToPointer(models.Thumbnail{
            Height:               1000,
            Url:                  "https://image.shutterstock.com/z/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
            Width:                1500,
        }),
        SmallThumb:           models.ToPointer(models.Thumbnail{
            Height:               67,
            Url:                  "https://thumb7.shutterstock.com/thumb_small/250738318/1572478477/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
            Width:                100,
        }),
    }

}
```

