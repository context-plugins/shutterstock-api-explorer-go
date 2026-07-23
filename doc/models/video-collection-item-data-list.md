
# Video Collection Item Data List

List of items in a collection

## Structure

`VideoCollectionItemDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.CollectionItem`](../../doc/models/collection-item.md) | Optional | Assets in the collection |
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
    videoCollectionItemDataList := models.VideoCollectionItemDataList{
        Data:                 []models.CollectionItem{
            models.CollectionItem{
                AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2016-08-18T18:52:59-04:00", func(err error) { log.Fatalln(err) })),
                Id:                   "76688182",
                MediaType:            models.ToPointer("video"),
            },
            models.CollectionItem{
                AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2016-08-18T18:52:59-04:00", func(err error) { log.Fatalln(err) })),
                Id:                   "40005859",
                MediaType:            models.ToPointer("video"),
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
    }

}
```

