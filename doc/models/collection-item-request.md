
# Collection Item Request

Request to get a list of items in a collection

## Structure

`CollectionItemRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Items` | [`[]models.CollectionItem`](../../doc/models/collection-item.md) | Required | List of items |

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
    collectionItemRequest := models.CollectionItemRequest{
        Items:                []models.CollectionItem{
            models.CollectionItem{
                AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) })),
                Id:                   "1690105108",
                MediaType:            models.ToPointer("image"),
            },
        },
    }

}
```

