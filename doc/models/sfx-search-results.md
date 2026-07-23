
# SFX Search Results

Sound effects search results

## Structure

`SFXSearchResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.SFX`](../../doc/models/sfx.md) | Required | List of tracks |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |
| `SearchId` | `string` | Required | ID of the search |
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
    sFXSearchResults := models.SFXSearchResults{
        Data:                 []models.SFX{
            models.SFX{
                AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2022-07-29", func(err error) { log.Fatalln(err) })),
                AffiliateUrl:         models.ToPointer("affiliate_url6"),
                Artist:               models.ToPointer("artist8"),
                Assets:               models.ToPointer(models.SFXAssets{
                    PreviewMp3:           models.ToPointer(models.SFXAssetDetails{
                        FileSize:             models.ToPointer(54),
                        Url:                  models.ToPointer("https://cdn.shutterstock.com/shutterstock/sfx/21230/preview_ecom_ster/heavy-duty-interface-feedback.mp3"),
                    }),
                    Waveform:             models.ToPointer(models.SFXAssetDetails{
                        FileSize:             models.ToPointer(74),
                        Url:                  models.ToPointer("https://cdn.shutterstock.com/shutterstock/sfx/21230/wvfm_img/heavy-duty-interface-feedback.png"),
                    }),
                }),
                Contributor:          models.Contributor{
                    Id:                   "321402911",
                },
                Description:          models.ToPointer("User interface calculations, scanning, thinking, text displayed on screen. Screen gak or garble."),
                Id:                   "123",
                MediaType:            "sfx",
                Title:                models.ToPointer("Heavy Duty Interface Feedback"),
                UpdatedTime:          models.ToPointer(parseTime(time.RFC3339, "2022-08-04T15:11:15.711Z", func(err error) { log.Fatalln(err) })),
            },
        },
        Message:              models.ToPointer("message6"),
        Page:                 models.ToPointer(50),
        PerPage:              models.ToPointer(218),
        SearchId:             "e6f84c4c-ffdd-499b-ad89-72c65a896ead",
        TotalCount:           14881,
    }

}
```

