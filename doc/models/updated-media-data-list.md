
# Updated Media Data List

List of updated media

## Structure

`UpdatedMediaDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.UpdatedMedia`](../../doc/models/updated-media.md) | Optional | Updated media items |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |
| `TotalCount` | `*int` | Optional | Total count of all results across all pages |

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
    updatedMediaDataList := models.UpdatedMediaDataList{
        Data:                 []models.UpdatedMedia{
            models.UpdatedMedia{
                Id:                   "123456789",
                UpdatedTime:          parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) }),
                Updates:              []string{
                    "addition",
                    "edit",
                },
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
        PerPage:              models.ToPointer(5),
        TotalCount:           models.ToPointer(13),
    }

}
```

