
# Editorial Video Search Results

Editorial search results

## Structure

`EditorialVideoSearchResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.EditorialVideoContent`](../../doc/models/editorial-video-content.md) | Required | Editorial items |
| `Message` | `*string` | Optional | Optional error message |
| `Next` | `*string` | Optional | Cursor value that represents the next page of results |
| `Page` | `*int` | Optional | Current page of the response |
| `PerPage` | `*int` | Optional | Number of results per page |
| `Prev` | `*string` | Optional | Cursor value that represents the previous page of results |
| `SearchId` | `*string` | Optional | Unique identifier for the search request |
| `TotalCount` | `int` | Required | Total count of all results |

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
    editorialVideoSearchResults := models.EditorialVideoSearchResults{
        Data:                 []models.EditorialVideoContent{
            models.EditorialVideoContent{
                Aspect:               models.ToPointer(float64(1)),
                Assets:               models.ToPointer(models.EditorialVideoAssets{
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
                }),
                Byline:               models.ToPointer("ViralHog/Shutterstock"),
                Caption:              models.ToPointer(""),
                Categories:           []models.EditorialCategory{
                },
                DateTaken:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2020-11-13", func(err error) { log.Fatalln(err) })),
                Description:          models.ToPointer("Info from Licensor: \"Peeps the Canadian Goose has been raised with our family since a gosling. Peeps has made appearances on our local news channels, TV shows, and local newspapers. He has been trained to fly next to four wheelers, jet ski's, and boats. He has brought joy to many people during the pandemic including those with cancer.\""),
                Id:                   "10679854a",
                Keywords:             []string{
                    "2020",
                    "adorable",
                    "birds",
                    "bizarre",
                    "canadian goose",
                    "cute",
                    "domesticated animals",
                    "entertainment",
                    "feel good",
                    "flew",
                    "flies",
                    "fly",
                    "flying",
                    "fun",
                    "goose",
                    "jet skis",
                    "nature",
                    "odd",
                    "pets",
                    "played",
                    "playing",
                    "plays",
                    "prior lake",
                    "sports",
                    "strange",
                    "sweet",
                    "usa",
                    "viralhog",
                    "virals",
                    "water sports",
                    "weird",
                },
                Title:                models.ToPointer("Peeps the Goose Has a Blast on a Jet Ski, Prior Lake, Minnesota, USA - 13 Nov 2020"),
            },
        },
        Message:              models.ToPointer("message0"),
        Next:                 models.ToPointer("eyJ2IjoyLCJzIjoyMCwicCI6WzBdfQ=="),
        Page:                 models.ToPointer(162),
        PerPage:              models.ToPointer(1),
        Prev:                 models.ToPointer(""),
        SearchId:             models.ToPointer("zhmz9zLmpQehdTPvg8cacQ"),
        TotalCount:           331,
    }

}
```

