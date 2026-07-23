
# Subscription Data List

List of subscriptions

## Structure

`SubscriptionDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Subscription`](../../doc/models/subscription.md) | Optional | Subscriptions retrieved from this user |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Optional error message |
| `Page` | `*int` | Optional | Current page that is being queried |
| `PerPage` | `*int` | Optional | Amount of subscriptions to show per page |
| `TotalCount` | `*int` | Optional | Total number of subscriptions for this user |

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
    subscriptionDataList := models.SubscriptionDataList{
        Data:                 []models.Subscription{
            models.Subscription{
                Allotment:            models.ToPointer(models.Allotment{
                    DownloadsLeft:        models.ToPointer(5),
                    DownloadsLimit:       models.ToPointer(10),
                    EndTime:              models.ToPointer(parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) })),
                    StartTime:            models.ToPointer(parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) })),
                }),
                AssetType:            models.ToPointer("images"),
                Description:          models.ToPointer("Annual Subscription"),
                ExpirationTime:       models.ToPointer(parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) })),
                Formats:              []models.LicenseFormat{
                    models.LicenseFormat{
                        Description:          models.ToPointer("Small"),
                        Format:               models.ToPointer("jpg"),
                        MediaType:            models.ToPointer(models.MediaTypeEnum_IMAGE),
                        MinResolution:        models.ToPointer(500),
                        Size:                 models.ToPointer("small"),
                    },
                    models.LicenseFormat{
                        Description:          models.ToPointer("Med"),
                        Format:               models.ToPointer("jpg"),
                        MediaType:            models.ToPointer(models.MediaTypeEnum_IMAGE),
                        MinResolution:        models.ToPointer(1000),
                        Size:                 models.ToPointer("medium"),
                    },
                    models.LicenseFormat{
                        Description:          models.ToPointer("Vector"),
                        Format:               models.ToPointer("eps"),
                        MediaType:            models.ToPointer(models.MediaTypeEnum_IMAGE),
                        MinResolution:        models.ToPointer(8),
                        Size:                 models.ToPointer("vector"),
                    },
                },
                Id:                   "s8906043",
                License:              models.ToPointer("standard"),
                Metadata:             models.ToPointer(interface{}("")),
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

