
# Keyword Data List

List of keywords

## Structure

`KeywordDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | `[]string` | Optional | Keywords |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    keywordDataList := models.KeywordDataList{
        Data:                 []string{
            "nature",
            "wildlife",
            "animal",
            "cute",
            "bamboo",
            "panda",
            "china",
            "wild",
            "endangered",
            "black",
            "bear",
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
        Message:              models.ToPointer("message4"),
    }

}
```

