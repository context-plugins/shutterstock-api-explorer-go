
# Featured Collection

Metadata about a featured collection

## Structure

`FeaturedCollection`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CoverItem` | [`*models.FeaturedCollectionCoverItem`](../../doc/models/featured-collection-cover-item.md) | Optional | Featured collection cover item metadata |
| `CreatedTime` | `*time.Time` | Optional | Date that the collection was created |
| `HeroItem` | [`*models.FeaturedCollectionCoverItem`](../../doc/models/featured-collection-cover-item.md) | Optional | Featured collection cover item metadata |
| `Id` | `string` | Required | Collection ID |
| `ItemsUpdatedTime` | `*time.Time` | Optional | Date that an item in the collection was last added or removed |
| `Name` | `string` | Required | Name of the collection |
| `ShareUrl` | `*string` | Optional | Unique share url for the collection |
| `TotalItemCount` | `int` | Required | Total number of items in the collection |
| `UpdatedTime` | `*time.Time` | Optional | Date that the collection was last modified |

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
    featuredCollection := models.FeaturedCollection{
        CoverItem:            models.ToPointer(models.FeaturedCollectionCoverItem{
            Url:                  "https://ak.picdn.net/assets/cms/b467415246debdab45825d915a548f8f79b57882-Collection_1_Thumnail.jpg",
        }),
        CreatedTime:          models.ToPointer(parseTime(time.RFC3339, "2021-07-07T13:10:24.000Z", func(err error) { log.Fatalln(err) })),
        HeroItem:             nil,
        Id:                   "19853",
        ItemsUpdatedTime:     models.ToPointer(parseTime(time.RFC3339, "2021-07-08T12:33:37.000Z", func(err error) { log.Fatalln(err) })),
        Name:                 "Exercise & Fitness",
        ShareUrl:             models.ToPointer("share_url0"),
        TotalItemCount:       82,
        UpdatedTime:          models.ToPointer(parseTime(time.RFC3339, "2021-07-07T13:10:24.000Z", func(err error) { log.Fatalln(err) })),
    }

}
```

