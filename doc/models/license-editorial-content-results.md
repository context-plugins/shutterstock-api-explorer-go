
# License Editorial Content Results

List of editorial license results

## Structure

`LicenseEditorialContentResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.LicenseEditorialContentResult`](../../doc/models/license-editorial-content-result.md) | Optional | License results |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Optional error message |
| `Page` | `*int` | Optional | Current page of the response |
| `PerPage` | `*int` | Optional | Number of results per page |
| `TotalCount` | `*int` | Optional | Total count of all results |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseEditorialContentResults := models.LicenseEditorialContentResults{
        Data:                 []models.LicenseEditorialContentResult{
            models.LicenseEditorialContentResult{
                AllotmentCharge:      models.ToPointer(1),
                Download:             models.ToPointer(models.Url{
                    Url:                  "https://s3-eu-west-1.amazonaws.com/api-downloads.rexfeatures.com/[random-characters].jpg?Expires=1524717323",
                }),
                EditorialId:          "69656358",
                Error:                models.ToPointer("error4"),
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
        Message:              models.ToPointer("message6"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(1),
        TotalCount:           models.ToPointer(12),
    }

}
```

