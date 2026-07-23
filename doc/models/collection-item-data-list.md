
# Collection Item Data List

List of items in a collection

## Structure

`CollectionItemDataList`

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
    collectionItemDataList := models.CollectionItemDataList{
        Data:                 []models.CollectionItem{
            models.CollectionItem{
                AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2021-07-08T12:33:37.000Z", func(err error) { log.Fatalln(err) })),
                Id:                   "1690105108",
                MediaType:            models.ToPointer("image"),
            },
            models.CollectionItem{
                AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2021-07-08T12:31:43.000Z", func(err error) { log.Fatalln(err) })),
                Id:                   "1468703072",
                MediaType:            models.ToPointer("image"),
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
        Message:              models.ToPointer("message0"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(2),
        TotalCount:           models.ToPointer(82),
    }

}
```

