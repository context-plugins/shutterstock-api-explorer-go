
# License SFX

## Structure

`LicenseSFX`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AudioLayout` | [`*models.AudioLayoutEnum`](../../doc/models/audio-layout-enum.md) | Optional | - |
| `Format` | [`*models.Format3Enum`](../../doc/models/format-3-enum.md) | Optional | - |
| `SearchId` | `*string` | Optional | ID of the search that led to this licensing event |
| `SfxId` | `string` | Required | ID of the sounds effect being licensed |
| `SubscriptionId` | `string` | Required | ID of the subscription to use for the download. |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseSFX := models.LicenseSFX{
        AudioLayout:          models.ToPointer(models.AudioLayoutEnum_STEREO),
        Format:               models.ToPointer(models.Format3Enum_WAV),
        SearchId:             models.ToPointer("search_id0"),
        SfxId:                "123456789",
        SubscriptionId:       "s12345678",
    }

}
```

