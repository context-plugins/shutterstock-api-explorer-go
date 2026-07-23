
# Editorial Image Livefeed List

List of editorial livefeeds

## Structure

`EditorialImageLivefeedList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.EditorialLivefeed`](../../doc/models/editorial-livefeed.md) | Required | Editorial livefeeds |
| `Message` | `*string` | Optional | Optional error message |
| `Page` | `*int` | Optional | Current page of the response |
| `PerPage` | `*int` | Optional | Number of results per page |
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
    editorialImageLivefeedList := models.EditorialImageLivefeedList{
        Data:                 []models.EditorialLivefeed{
            models.EditorialLivefeed{
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
            },
        },
        Message:              models.ToPointer("message6"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(1),
        TotalCount:           5300,
    }

}
```

