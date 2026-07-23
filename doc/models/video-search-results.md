
# Video Search Results

Video search results

## Structure

`VideoSearchResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Video`](../../doc/models/video.md) | Required | List of videos |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |
| `SearchId` | `string` | Required | Unique identifier for the search request |
| `TotalCount` | `int` | Required | Total count of all results across all pages |

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
    videoSearchResults := models.VideoSearchResults{
        Data:                 []models.Video{
            models.Video{
                AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
                AffiliateUrl:         models.ToPointer("affiliate_url6"),
                Aspect:               models.ToPointer(float64(1.778)),
                AspectRatio:          models.ToPointer("16:9"),
                Assets:               models.ToPointer(models.VideoAssets{
                    M4k:                  nil,
                    Hd:                   nil,
                    PreviewJpg:           models.ToPointer(models.Url{
                        Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/12.jpg",
                    }),
                    PreviewMp4:           models.ToPointer(models.Url{
                        Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/preview/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.mp4",
                    }),
                    PreviewWebm:          models.ToPointer(models.Url{
                        Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/preview/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.webm",
                    }),
                    ThumbJpg:             models.ToPointer(models.Url{
                        Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/12.jpg",
                    }),
                    ThumbMp4:             models.ToPointer(models.Url{
                        Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.mp4",
                    }),
                    ThumbWebm:            models.ToPointer(models.Url{
                        Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.webm",
                    }),
                }),
                Contributor:          models.Contributor{
                    Id:                   "4411978",
                },
                Description:          models.ToPointer("Camera follows hipster millennial young woman in orange jacket running up on top of mountain summit at sunset, jumps on top of rocks, raises arms into air, happy and drunk on life, youth and happiness"),
                Duration:             models.ToPointer(float64(14.081)),
                HasModelRelease:      models.ToPointer(true),
                Id:                   "1033184651",
                MediaType:            "video",
            },
        },
        Message:              models.ToPointer("message0"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(5),
        SearchId:             "749090bb-2967-4a20-b22e-c800dc845e10",
        TotalCount:           123,
    }

}
```

