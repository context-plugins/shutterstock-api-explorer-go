
# License Video Result Data List

List of video license results

## Structure

`LicenseVideoResultDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.LicenseVideoResult`](../../doc/models/license-video-result.md) | Optional | License results |
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
    licenseVideoResultDataList := models.LicenseVideoResultDataList{
        Data:                 []models.LicenseVideoResult{
            models.LicenseVideoResult{
                AllotmentCharge:      models.ToPointer(1),
                Download:             models.ToPointer(models.Url{
                    Url:                  "https://download.shutterstock.com/gatekeeper/[random-characters]/shutterstock_59656357.mp4",
                }),
                Error:                models.ToPointer("error4"),
                LicenseId:            models.ToPointer("license_id6"),
                Price:                models.ToPointer(models.Price{
                    LocalAmount:          models.ToPointer(float64(12.34)),
                    LocalCurrency:        models.ToPointer("EUR"),
                }),
                VideoId:              "123456789",
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
        Message:              models.ToPointer("message8"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(5),
        TotalCount:           models.ToPointer(123455),
    }

}
```

