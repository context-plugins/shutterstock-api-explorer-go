
# Editorial Image Livefeed

Metadata about editorial livefeed

## Structure

`EditorialImageLivefeed`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CoverItem` | [`*models.EditorialCoverItem`](../../doc/models/editorial-cover-item.md) | Optional | Cover image for editorial livefeed |
| `CreatedTime` | `*time.Time` | Optional | When the livefeed was initially created |
| `Id` | `string` | Required | Livefeed ID |
| `Name` | `string` | Required | Name of the livefeed |
| `TotalItemCount` | `int` | Required | Total count of items in the livefeed |

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
    editorialImageLivefeed := models.EditorialImageLivefeed{
        CoverItem:            models.ToPointer(models.EditorialCoverItem{
            Height:               models.ToPointer(117),
            Id:                   "9763363q",
            Url:                  "https://editorial01.qa.shuttercorp.net/thumb/9763363q/51e28f39/Shutterstock_9763363q.jpg",
            Width:                models.ToPointer(170),
        }),
        CreatedTime:          models.ToPointer(parseTime(time.RFC3339, "2018-07-17T12:42:03+00:00", func(err error) { log.Fatalln(err) })),
        Id:                   "2018%2F07%2F17%2FPrince%20Charles%20and%20Camilla%20Duchess%20of%20Cornwall%20visit%20to%20Cornwall%2C%20Day%202",
        Name:                 "Prince Charles and Camilla Duchess of Cornwall visit to Cornwall, Day 2",
        TotalItemCount:       38,
    }

}
```

