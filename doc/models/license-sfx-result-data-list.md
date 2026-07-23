
# License SFX Result Data List

List of information about licensed sound effects

## Structure

`LicenseSFXResultDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.LicenseSFXResult`](../../doc/models/license-sfx-result.md) | Optional | Sound effects license results |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseSFXResultDataList := models.LicenseSFXResultDataList{
        Data:                 []models.LicenseSFXResult{
            models.LicenseSFXResult{
                AllotmentCharge:      models.ToPointer(1),
                Download:             models.ToPointer(models.Url{
                    Url:                  "https://download.shutterstock.com/gatekeeper/[random-characters]/shutterstock_59656357.mp3",
                }),
                Error:                models.ToPointer("error4"),
                LicenseId:            models.ToPointer("license_id6"),
                SfxId:                "123456789",
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
        Message:              models.ToPointer("message2"),
    }

}
```

