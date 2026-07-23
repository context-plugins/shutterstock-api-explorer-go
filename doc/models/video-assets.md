
# Video Assets

Video asset information

## Structure

`VideoAssets`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `M4k` | [`*models.VideoSizeDetails`](../../doc/models/video-size-details.md) | Optional | Video asset information |
| `Hd` | [`*models.VideoSizeDetails`](../../doc/models/video-size-details.md) | Optional | Video asset information |
| `PreviewJpg` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `PreviewMp4` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `PreviewWebm` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `Sd` | [`*models.VideoSizeDetails`](../../doc/models/video-size-details.md) | Optional | Video asset information |
| `ThumbJpg` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `ThumbJpgs` | [`*models.Urls`](../../doc/models/urls.md) | Optional | List of URLs |
| `ThumbMp4` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `ThumbWebm` | [`*models.Url`](../../doc/models/url.md) | Optional | URL object |
| `Web` | [`*models.VideoSizeDetails`](../../doc/models/video-size-details.md) | Optional | Video asset information |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    videoAssets := models.VideoAssets{
        M4k:                  nil,
        Hd:                   models.ToPointer(models.VideoSizeDetails{
            DisplayName:          models.ToPointer("Original HD"),
            FileSize:             models.ToPointer(110359552),
            Format:               models.ToPointer("avc1"),
            Fps:                  models.ToPointer(float64(29.97)),
            Height:               models.ToPointer(1080),
            IsLicensable:         models.ToPointer(true),
            Width:                models.ToPointer(1920),
        }),
        PreviewJpg:           models.ToPointer(models.Url{
            Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/12.jpg",
        }),
        PreviewMp4:           models.ToPointer(models.Url{
            Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/preview/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.mp4",
        }),
        PreviewWebm:          models.ToPointer(models.Url{
            Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/preview/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.webm",
        }),
        Sd:                   models.ToPointer(models.VideoSizeDetails{
            DisplayName:          models.ToPointer("Standard Definition MPEG"),
            FileSize:             models.ToPointer(4577280),
            Format:               models.ToPointer("mov"),
            Fps:                  models.ToPointer(float64(29.97)),
            Height:               models.ToPointer(480),
            IsLicensable:         models.ToPointer(true),
            Width:                models.ToPointer(852),
        }),
        ThumbJpg:             models.ToPointer(models.Url{
            Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/12.jpg",
        }),
        ThumbJpgs:            models.ToPointer(models.Urls{
            Urls:                 []string{
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/1.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/2.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/3.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/4.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/5.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/6.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/7.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/8.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/9.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/10.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/11.jpg",
                "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/12.jpg",
            },
        }),
        ThumbMp4:             models.ToPointer(models.Url{
            Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.mp4",
        }),
        ThumbWebm:            models.ToPointer(models.Url{
            Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.webm",
        }),
        Web:                  models.ToPointer(models.VideoSizeDetails{
            DisplayName:          models.ToPointer("Low Resolution MPEG"),
            FileSize:             models.ToPointer(1291264),
            Format:               models.ToPointer("mov"),
            Fps:                  models.ToPointer(float64(29.97)),
            Height:               models.ToPointer(240),
            IsLicensable:         models.ToPointer(true),
            Width:                models.ToPointer(426),
        }),
    }

}
```

