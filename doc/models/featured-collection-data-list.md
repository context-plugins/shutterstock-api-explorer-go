
# Featured Collection Data List

List of featured collections

## Structure

`FeaturedCollectionDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.FeaturedCollection`](../../doc/models/featured-collection.md) | Optional | Featured collections |
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
    featuredCollectionDataList := models.FeaturedCollectionDataList{
        Data:                 []models.FeaturedCollection{
            models.FeaturedCollection{
                CoverItem:            models.ToPointer(models.FeaturedCollectionCoverItem{
                    Url:                  "https://ak.picdn.net/assets/cms/b467415246debdab45825d915a548f8f79b57882-Collection_1_Thumnail.jpg",
                }),
                CreatedTime:          models.ToPointer(parseTime(time.RFC3339, "2021-07-07T13:10:24.000Z", func(err error) { log.Fatalln(err) })),
                HeroItem:             nil,
                Id:                   "19853",
                ItemsUpdatedTime:     models.ToPointer(parseTime(time.RFC3339, "2021-07-08T12:33:37.000Z", func(err error) { log.Fatalln(err) })),
                Name:                 "Exercise & Fitness",
                ShareUrl:             models.ToPointer("share_url4"),
                TotalItemCount:       82,
                UpdatedTime:          models.ToPointer(parseTime(time.RFC3339, "2021-07-07T13:10:24.000Z", func(err error) { log.Fatalln(err) })),
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
        TotalCount:           models.ToPointer(123455),
    }

}
```

