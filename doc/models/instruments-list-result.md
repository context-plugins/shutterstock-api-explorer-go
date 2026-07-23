
# Instruments List Result

Image search results

## Structure

`InstrumentsListResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Instrument`](../../doc/models/instrument.md) | Optional | List of instrumnets |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    instrumentsListResult := models.InstrumentsListResult{
        Data:                 []models.Instrument{
            models.Instrument{
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
            },
        },
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(5),
    }

}
```

