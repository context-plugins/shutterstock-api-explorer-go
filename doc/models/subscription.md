
# Subscription

Subscription information

## Structure

`Subscription`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Allotment` | [`*models.Allotment`](../../doc/models/allotment.md) | Optional | An allotment of credits as part of a subscription |
| `AssetType` | `*string` | Optional | Identifier for the type of assets associated with this subscription (images, videos, audio, editorial) |
| `Description` | `*string` | Optional | Description of the subscription |
| `ExpirationTime` | `*time.Time` | Optional | Date the subscription ends |
| `Formats` | [`[]models.LicenseFormat`](../../doc/models/license-format.md) | Optional | List of formats that are licensable for the subscription |
| `Id` | `string` | Required | Unique internal identifier for the subscription |
| `License` | `*string` | Optional | Internal identifier for the type of subscription |
| `Metadata` | `*interface{}` | Optional | Subscription metadata; different for each customer |
| `PricePerDownload` | [`*models.Price`](../../doc/models/price.md) | Optional | Price |

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
    subscription := models.Subscription{
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
    }

}
```

