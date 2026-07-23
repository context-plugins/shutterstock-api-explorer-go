
# Recommendation Data List

List of recommended images

## Structure

`RecommendationDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Recommendation`](../../doc/models/recommendation.md) | Optional | Recommended images |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |
| `TotalCount` | `*int` | Optional | Total count of all results across all pages |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    recommendationDataList := models.RecommendationDataList{
        Data:                 []models.Recommendation{
            models.Recommendation{
                Id:                   "123456789",
            },
            models.Recommendation{
                Id:                   "99379946",
            },
            models.Recommendation{
                Id:                   "133918412",
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
        TotalCount:           models.ToPointer(12),
    }

}
```

