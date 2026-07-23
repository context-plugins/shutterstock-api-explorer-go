
# Editorial Assets

Asset information, including size and thumbnail URLs

## Structure

`EditorialAssets`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `MediumJpg` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |
| `Original` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |
| `SmallJpg` | [`*models.ImageSizeDetails`](../../doc/models/image-size-details.md) | Optional | Image size information |
| `Thumb170` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `Thumb220` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `Watermark1500` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |
| `Watermark450` | [`*models.Thumbnail`](../../doc/models/thumbnail.md) | Optional | Image thumbnail information |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    editorialAssets := models.EditorialAssets{
        MediumJpg:            models.ToPointer(models.ImageSizeDetails{
            DisplayName:          models.ToPointer("Med"),
            Dpi:                  models.ToPointer(6),
            FileSize:             models.ToPointer(254),
            Format:               models.ToPointer("format4"),
            Height:               models.ToPointer(617),
            IsLicensable:         models.ToPointer(true),
            Width:                models.ToPointer(1000),
        }),
        Original:             models.ToPointer(models.ImageSizeDetails{
            DisplayName:          models.ToPointer("Original"),
            Dpi:                  models.ToPointer(44),
            FileSize:             models.ToPointer(36),
            Format:               models.ToPointer("format6"),
            Height:               models.ToPointer(3693),
            IsLicensable:         models.ToPointer(true),
            Width:                models.ToPointer(5985),
        }),
        SmallJpg:             models.ToPointer(models.ImageSizeDetails{
            DisplayName:          models.ToPointer("Small"),
            Dpi:                  models.ToPointer(100),
            FileSize:             models.ToPointer(92),
            Format:               models.ToPointer("format8"),
            Height:               models.ToPointer(309),
            IsLicensable:         models.ToPointer(true),
            Width:                models.ToPointer(500),
        }),
        Thumb170:             models.ToPointer(models.Thumbnail{
            Height:               105,
            Url:                  "https://editorial01.qa.shuttercorp.net/thumb/10687730b/272a999e/Shutterstock_10687730b.jpg",
            Width:                170,
        }),
        Thumb220:             models.ToPointer(models.Thumbnail{
            Height:               136,
            Url:                  "https://editorial01.qa.shuttercorp.net/thumb-220/10687730b/927a6ebe/Shutterstock_10687730b.jpg",
            Width:                220,
        }),
        Watermark1500:        models.ToPointer(models.Thumbnail{
            Height:               926,
            Url:                  "https://editorial01.qa.shuttercorp.net/wm-preview-1500/10687730b/ee2d7ae1/Shutterstock_10687730b.jpg",
            Width:                1500,
        }),
        Watermark450:         models.ToPointer(models.Thumbnail{
            Height:               278,
            Url:                  "https://editorial01.qa.shuttercorp.net/wm-preview-450/10687730b/ff2443ad/Shutterstock_10687730b.jpg",
            Width:                450,
        }),
    }

}
```

