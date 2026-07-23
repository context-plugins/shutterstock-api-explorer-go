
# Category Data List

List of categories that images can belong to

## Structure

`CategoryDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Category`](../../doc/models/category.md) | Optional | Categories |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | The current page of results |
| `PerPage` | `*int` | Optional | The number of results per page |
| `TotalCount` | `*int` | Optional | The total number of results across all pages |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    categoryDataList := models.CategoryDataList{
        Data:                 []models.Category{
            models.Category{
                Id:                   models.ToPointer("1"),
                Name:                 models.ToPointer("Animals/Wildlife"),
            },
            models.Category{
                Id:                   models.ToPointer("11"),
                Name:                 models.ToPointer("The Arts"),
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
        Message:              models.ToPointer("message8"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(2),
        TotalCount:           models.ToPointer(13),
    }

}
```

