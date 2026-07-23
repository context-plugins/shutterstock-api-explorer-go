
# License Audio Request

Audio license request data

## Structure

`LicenseAudioRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Audio` | [`[]models.LicenseAudio`](../../doc/models/license-audio.md) | Required | List of audio tracks to license<br><br>**Constraints**: *Maximum Items*: `50` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseAudioRequest := models.LicenseAudioRequest{
        Audio:                []models.LicenseAudio{
            models.LicenseAudio{
                AudioId:              "591623",
                License:              models.ToPointer(models.License1Enum_AUDIOPLATFORM),
                SearchId:             models.ToPointer("search_id8"),
            },
        },
    }

}
```

