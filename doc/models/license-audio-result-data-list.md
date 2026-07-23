
# License Audio Result Data List

List of audio license results

## Structure

`LicenseAudioResultDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.LicenseAudioResult`](../../doc/models/license-audio-result.md) | Optional | License results |
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
    licenseAudioResultDataList := models.LicenseAudioResultDataList{
        Data:                 []models.LicenseAudioResult{
            models.LicenseAudioResult{
                AllotmentCharge:      models.ToPointer(float64(1)),
                AudioId:              "123456789",
                Download:             models.ToPointer(models.AudioUrl{
                    ShortsLoopsStems:     models.ToPointer("shorts_loops_stems4"),
                    Url:                  "http://download2.dev.shutterstock.com/gatekeeper/abc/original.wav",
                }),
                Error:                models.ToPointer("error4"),
                LicenseId:            models.ToPointer("abcdef123456789ghijklmn"),
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
        Message:              models.ToPointer("message6"),
        Page:                 models.ToPointer(250),
        PerPage:              models.ToPointer(162),
    }

}
```

