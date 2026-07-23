
# Download History

Information about a downloaded media item. Applicable for all media types, only one of 'audio', 'image' or 'video' will be in a single DownloadHistory object

## Structure

`DownloadHistory`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Audio` | [`*models.DownloadHistoryMediaDetails`](../../doc/models/download-history-media-details.md) | Optional | Information about the downloaded media |
| `DownloadTime` | `time.Time` | Required | Date the media was downloaded the first time |
| `Id` | `string` | Required | ID of the download |
| `Image` | [`*models.DownloadHistoryMediaDetails`](../../doc/models/download-history-media-details.md) | Optional | Information about the downloaded media |
| `IsDownloadable` | `*bool` | Optional | Specifies if the media is downloadable via its respective downloads endpoint |
| `License` | `string` | Required | The name of the license of this download |
| `Metadata` | `*interface{}` | Optional | The metadata that was passed in the original licensing request |
| `Revshare` | [`*models.DownloadHistoryRevshareDetails`](../../doc/models/download-history-revshare-details.md) | Optional | Pricing information for revenue-sharing transactions |
| `SubscriptionId` | `*string` | Optional | ID of the subscription used to perform this download |
| `User` | [`*models.DownloadHistoryUserDetails`](../../doc/models/download-history-user-details.md) | Optional | Information about a user |
| `Video` | [`*models.DownloadHistoryMediaDetails`](../../doc/models/download-history-media-details.md) | Optional | Information about the downloaded media |

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
    downloadHistory := models.DownloadHistory{
        Audio:                nil,
        DownloadTime:         parseTime(time.RFC3339, "2021-05-20T20:31:46.000Z", func(err error) { log.Fatalln(err) }),
        Id:                   "a24499ca3ccd912a6d8316d45f953ef092",
        Image:                models.ToPointer(models.DownloadHistoryMediaDetails{
            Format:               models.ToPointer(models.DownloadHistoryFormatDetails{
                Format:               models.ToPointer("format0"),
                Size:                 models.ToPointer("medium"),
            }),
            Id:                   "1234567",
        }),
        IsDownloadable:       models.ToPointer(true),
        License:              "standard",
        Metadata:             models.ToPointer(interface{}("[key1, val1][key2, val2]")),
        Revshare:             nil,
        SubscriptionId:       models.ToPointer("s12345678"),
        User:                 models.ToPointer(models.DownloadHistoryUserDetails{
            Username:             "jdoe",
        }),
    }

}
```

