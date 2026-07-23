
# Instrument

Information about an musical instrument

## Structure

`Instrument`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*string` | Optional | The id of the instrument |
| `Name` | `*string` | Optional | Name of the instrument |
| `Previews` | [`[]models.Preview`](../../doc/models/preview.md) | Optional | Preview of the instrument |
| `Tags` | `[]string` | Optional | List of tags |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    instrument := models.Instrument{
        Id:                   models.ToPointer("bright_roomy_kit"),
        Name:                 models.ToPointer("Bright Roomy Kit"),
        Previews:             []models.Preview{
            models.Preview{
                ContentType:          models.ToPointer(models.ContentTypeEnum_ENUMAUDIOMP3),
                Url:                  models.ToPointer("https://public-cdn.ampermusic.com/instruments/previews/bright_roomy_kit_v1.mp3"),
            },
        },
        Tags:                 []string{
            "Percussion",
            "Aux Percs",
            "Set Cymbals",
            "Crash",
            "Open",
            "Ride",
            "Set Hi-Hat",
            "Set Kicks",
            "Stick Snare",
            "Quad Toms",
            "Roto Toms",
        },
    }

}
```

