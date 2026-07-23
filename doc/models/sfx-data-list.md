
# SFX Data List

List of sound effects

## Structure

`SFXDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.SFX`](../../doc/models/sfx.md) | Optional | Sound Effects |

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
    sFXDataList := models.SFXDataList{
        Data:                 []models.SFX{
            models.SFX{
                AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
                AffiliateUrl:         models.ToPointer("affiliate_url6"),
                Artist:               models.ToPointer("artist8"),
                Assets:               nil,
                Contributor:          models.Contributor{
                    Id:                   "1234",
                },
                Description:          models.ToPointer("description0"),
                Id:                   "123",
                MediaType:            "sfx",
            },
        },
    }

}
```

