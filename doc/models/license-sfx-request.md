
# License SFX Request

License sounds effect asset request body

## Structure

`LicenseSFXRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `SoundEffects` | [`[]models.LicenseSFX`](../../doc/models/license-sfx.md) | Required | Sound effects to license for |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseSFXRequest := models.LicenseSFXRequest{
        SoundEffects:         []models.LicenseSFX{
            models.LicenseSFX{
                AudioLayout:          models.ToPointer(models.AudioLayoutEnum_AMBISONIC),
                Format:               models.ToPointer(models.Format3Enum_WAV),
                SearchId:             models.ToPointer("search_id6"),
                SfxId:                "123456789",
                SubscriptionId:       "s12345678",
            },
        },
    }

}
```

