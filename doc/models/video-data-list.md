
# Video Data List

List of videos

## Structure

`VideoDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Video`](../../doc/models/video.md) | Optional | Videos |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |
| `TotalCount` | `*int` | Optional | Total count of all results across all pages |

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
    videoDataList := models.VideoDataList{
        Data:                 []models.Video{
            models.Video{
                AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2019-07-13", func(err error) { log.Fatalln(err) })),
                AffiliateUrl:         models.ToPointer("affiliate_url6"),
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
            },
        },
        Errors:               []models.Error{
            models.Error{
                Code:                 models.ToPointer("code8"),
                Data:                 models.ToPointer("data0"),
                Items:                []interface{}{
                    interface{}("[key1, val1][key2, val2]"),
                },
                Message:              "message0",
                Path:                 models.ToPointer("path4"),
            },
        },
        Message:              models.ToPointer("message4"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(5),
        TotalCount:           models.ToPointer(25),
    }

}
```

