
# Collection

Metadata about a collection of assets

## Structure

`Collection`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CoverItem` | [`*models.CollectionItem`](../../doc/models/collection-item.md) | Optional | Metadata about an item that is part of a collection |
| `CreatedTime` | `*time.Time` | Optional | When the collection was created |
| `Id` | `string` | Required | The collection ID |
| `ItemsUpdatedTime` | `*time.Time` | Optional | The last time this collection's items were updated |
| `Name` | `string` | Required | The name of the collection |
| `ShareCode` | `*string` | Optional | A code that can be used to share the collection (optional) |
| `ShareUrl` | `*string` | Optional | The browser URL that can be used to share the collection (optional) |
| `TotalItemCount` | `int` | Required | The number of items in the collection |
| `UpdatedTime` | `*time.Time` | Optional | The last time the collection was update (other than changes to the items in it) |

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
    collection := models.Collection{
        CoverItem:            models.ToPointer(models.CollectionItem{
            AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
            Id:                   "297886754",
            MediaType:            models.ToPointer("media_type6"),
        }),
        CreatedTime:          models.ToPointer(parseTime(time.RFC3339, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
        Id:                   "293542904",
        ItemsUpdatedTime:     models.ToPointer(parseTime(time.RFC3339, "2021-05-20T16:15:22-04:00", func(err error) { log.Fatalln(err) })),
        Name:                 "My collection",
        ShareCode:            models.ToPointer("share_code2"),
        ShareUrl:             models.ToPointer("share_url0"),
        TotalItemCount:       85,
    }

}
```

