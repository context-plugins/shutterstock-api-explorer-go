
# License Audio Result

The response to a licensing request for an audio track

## Structure

`LicenseAudioResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AllotmentCharge` | `*float64` | Optional | Number of credits that this licensing event used |
| `AudioId` | `string` | Required | ID of the track that was licensed |
| `Download` | [`*models.AudioUrl`](../../doc/models/audio-url.md) | Optional | Audio License URL object |
| `Error` | `*string` | Optional | Error information if applicable |
| `LicenseId` | `*string` | Optional | ID of the license event |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseAudioResult := models.LicenseAudioResult{
        AllotmentCharge:      models.ToPointer(float64(1)),
        AudioId:              "123456789",
        Download:             models.ToPointer(models.AudioUrl{
            ShortsLoopsStems:     models.ToPointer("shorts_loops_stems4"),
            Url:                  "http://download2.dev.shutterstock.com/gatekeeper/abc/original.wav",
        }),
        Error:                models.ToPointer("error4"),
        LicenseId:            models.ToPointer("abcdef123456789ghijklmn"),
    }

}
```

