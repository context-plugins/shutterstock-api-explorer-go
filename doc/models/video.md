
# Video

Information about a video

## Structure

`Video`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AddedDate` | `*time.Time` | Optional | Date this video was added to the Shutterstock library |
| `AffiliateUrl` | `*string` | Optional | Affiliate referral link; appears only for registered affiliate partners |
| `Aspect` | `*float64` | Optional | Aspect ratio of this video in decimal format, such as 0.6667 |
| `AspectRatio` | `*string` | Optional | Aspect ratio of the video as a ratio, such as 16:9 |
| `Assets` | [`*models.VideoAssets`](../../doc/models/video-assets.md) | Optional | Video asset information |
| `Categories` | [`[]models.Category`](../../doc/models/category.md) | Optional | List of categories |
| `Contributor` | [`models.Contributor`](../../doc/models/contributor.md) | Required | Information about a contributor |
| `Description` | `*string` | Optional | Description of this video |
| `Duration` | `*float64` | Optional | Duration of this video, in seconds |
| `HasModelRelease` | `*bool` | Optional | Whether or not this video has been released for use by the model appearing in it |
| `HasPropertyRelease` | `*bool` | Optional | Whether or not this video has received a release to show the landmark or property appearing in it |
| `Id` | `string` | Required | ID of the video |
| `IsAdult` | `*bool` | Optional | Whether or not this video contains adult content |
| `IsEditorial` | `*bool` | Optional | Whether or not this video is editorial content |
| `Keywords` | `[]string` | Optional | Keywords associated with the content of this video |
| `MediaType` | `string` | Required | Media type of this video, should always be "video" |
| `Models` | [`[]models.Model`](../../doc/models/model.md) | Optional | List of models in this video |
| `Url` | `*string` | Optional | Link to video information page; included only for certain accounts |

## Example

```go
package main

import (
    "log"
    "time"
    "shutterstockapiexplorer/models"
)

func main() {
    parseTime := func(layout, value string, errCallback func(error)) time.Time {
        dateTime, err := time.Parse(layout, value)
        if err != nil {
            errCallback(err) 
       }
        return dateTime
    }
    video := models.Video{
        AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2019-07-13", func(err error) { log.Fatalln(err) })),
        AffiliateUrl:         models.ToPointer("affiliate_url2"),
        Aspect:               models.ToPointer(float64(1.778)),
        AspectRatio:          models.ToPointer("16:9"),
        Assets:               models.ToPointer(models.VideoAssets{
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
        }),
        Categories:           []models.Category{
            models.Category{
                Id:                   models.ToPointer("12"),
                Name:                 models.ToPointer("Nature"),
            },
            models.Category{
                Id:                   models.ToPointer("13"),
                Name:                 models.ToPointer("People"),
            },
        },
        Contributor:          models.Contributor{
            Id:                   "4411978",
        },
        Description:          models.ToPointer("Camera follows hipster millennial young woman in orange jacket running up on top of mountain summit at sunset, jumps on top of rocks, raises arms into air, happy and drunk on life, youth and happiness"),
        Duration:             models.ToPointer(float64(14.081)),
        HasModelRelease:      models.ToPointer(true),
        HasPropertyRelease:   models.ToPointer(false),
        Id:                   "1033184651",
        IsAdult:              models.ToPointer(false),
        IsEditorial:          models.ToPointer(false),
        Keywords:             []string{
            "active",
            "activity",
            "adventure",
            "arms",
            "backpacker",
            "carefree",
            "celebrating",
            "cliff",
            "climate",
            "cloud",
            "discovery",
            "escape",
            "explore",
            "extreme",
            "free",
            "freedom",
            "girl",
            "happy",
            "high",
            "hiker",
            "hiking",
            "hill",
            "independent",
            "inspiration",
            "landscape",
            "leisure",
            "lifestyle",
            "mountain",
            "mountains",
            "nature",
            "outdoor",
            "peak",
            "person",
            "rock",
            "scenic",
            "sky",
            "sport",
            "success",
            "summer",
            "summit",
            "sun",
            "sunset",
            "top",
            "tourism",
            "travel",
            "trekking",
            "vacation",
            "view",
            "winning",
            "woman",
        },
        MediaType:            "video",
        Models:               []models.Model{
            models.Model{
                Id:                   "33233810",
            },
            models.Model{
                Id:                   "25487168",
            },
        },
    }

}
```

