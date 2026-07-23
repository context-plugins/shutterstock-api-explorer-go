
# Download History Data List

List of download events

## Structure

`DownloadHistoryDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.DownloadHistory`](../../doc/models/download-history.md) | Optional | Download events |
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
    downloadHistoryDataList := models.DownloadHistoryDataList{
        Data:                 []models.DownloadHistory{
            models.DownloadHistory{
                Audio:                nil,
                DownloadTime:         parseTime(time.RFC3339, "2021-07-15T15:46:34.000Z", func(err error) { log.Fatalln(err) }),
                Id:                   "e1eba3833793e77188d22caae8bac9f2cd",
                Image:                models.ToPointer(models.DownloadHistoryMediaDetails{
                    Format:               models.ToPointer(models.DownloadHistoryFormatDetails{
                        Format:               models.ToPointer("format0"),
                        Size:                 models.ToPointer("original"),
                    }),
                    Id:                   "9763363ao",
                }),
                IsDownloadable:       models.ToPointer(false),
                License:              "premier_editorial_all_digital",
                Metadata:             models.ToPointer(interface{}("[client, Company A][job, Important project][other, Important media][purchase_order, 123456]")),
                Revshare:             nil,
                SubscriptionId:       models.ToPointer("s12345678"),
                User:                 models.ToPointer(models.DownloadHistoryUserDetails{
                    Username:             "editorial_test_account_002",
                }),
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
        PerPage:              models.ToPointer(1),
        TotalCount:           models.ToPointer(2890),
    }

}
```

