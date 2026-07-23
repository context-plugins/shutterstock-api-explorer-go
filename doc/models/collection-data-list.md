
# Collection Data List

List of collections

## Structure

`CollectionDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Collection`](../../doc/models/collection.md) | Optional | Collections |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | The current page of results |
| `PerPage` | `*int` | Optional | The number of results per page |
| `TotalCount` | `*int` | Optional | The total number of results across all pages |

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
    collectionDataList := models.CollectionDataList{
        Data:                 []models.Collection{
            models.Collection{
                CoverItem:            models.ToPointer(models.CollectionItem{
                    AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
                    Id:                   "297886754",
                    MediaType:            models.ToPointer("media_type6"),
                }),
                CreatedTime:          models.ToPointer(parseTime(time.RFC3339, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
                Id:                   "293542904",
                ItemsUpdatedTime:     models.ToPointer(parseTime(time.RFC3339, "2021-05-20T16:15:22-04:00", func(err error) { log.Fatalln(err) })),
                Name:                 "My collection",
                ShareCode:            models.ToPointer("share_code6"),
                ShareUrl:             models.ToPointer("share_url4"),
                TotalItemCount:       85,
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
        PerPage:              models.ToPointer(100),
        TotalCount:           models.ToPointer(1),
    }

}
```

