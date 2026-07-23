
# License Audio

An audio track in a licensing request

## Structure

`LicenseAudio`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AudioId` | `string` | Required | ID of the track being licensed |
| `License` | [`*models.License1Enum`](../../doc/models/license-1-enum.md) | Optional | Type of license |
| `SearchId` | `*string` | Optional | ID of the search that led to this licensing event |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseAudio := models.LicenseAudio{
        AudioId:              "123456789",
        License:              models.ToPointer(models.License1Enum_AUDIOPLATFORM),
        SearchId:             models.ToPointer("987654321"),
    }

}
```

