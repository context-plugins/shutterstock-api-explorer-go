
# License Image Result Data List

List of information about licensed images

## Structure

`LicenseImageResultDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.LicenseImageResult`](../../doc/models/license-image-result.md) | Optional | License results |
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
    licenseImageResultDataList := models.LicenseImageResultDataList{
        Data:                 []models.LicenseImageResult{
            models.LicenseImageResult{
                AllotmentCharge:      models.ToPointer(1),
                Download:             models.ToPointer(models.Url{
                    Url:                  "https://download.shutterstock.com/gatekeeper/[random-characters]/shutterstock_59656357.jpg",
                }),
                Error:                models.ToPointer("error4"),
                ImageId:              "59656357",
                LicenseId:            models.ToPointer("license_id6"),
                Price:                nil,
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
        Message:              models.ToPointer("message0"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(5),
        TotalCount:           models.ToPointer(23),
    }

}
```

