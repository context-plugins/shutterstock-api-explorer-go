
# Descriptors List Result

List Descriptors results

## Structure

`DescriptorsListResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Descriptors`](../../doc/models/descriptors.md) | Optional | List of descriptors |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    descriptorsListResult := models.DescriptorsListResult{
        Data:                 []models.Descriptors{
            models.Descriptors{
                AverageRenderSpeed:   models.ToPointer(float64(8.242664029014177)),
                Bands:                []models.Bands{
                    models.Bands{
                        Id:                   models.ToPointer("cinematic_minimal_tense_band_1"),
                        Name:                 models.ToPointer("Cinematic Minimal Tense Band 1"),
                    },
                    models.Bands{
                        Id:                   models.ToPointer("cinematic_minimal_tense_band_2"),
                        Name:                 models.ToPointer("Cinematic Minimal Tense Band 2"),
                    },
                },
                Id:                   models.ToPointer("cinematic_minimal_tense"),
                Instruments:          []models.Instruments{
                    models.Instruments{
                        Id:                   models.ToPointer("blue_synth_pad"),
                        Name:                 models.ToPointer("Warm Pad - Lush"),
                    },
                    models.Instruments{
                        Id:                   models.ToPointer("direct_round_1_synth_bass"),
                        Name:                 models.ToPointer("Direct Round 1 Synth Bass"),
                    },
                    models.Instruments{
                        Id:                   models.ToPointer("direct_crystal_breath_mid_pad"),
                        Name:                 models.ToPointer("Direct Crystal Breath Mid Pad"),
                    },
                },
                MaxTempo:             models.ToPointer(float64(76)),
                MinTempo:             models.ToPointer(float64(58)),
                Name:                 models.ToPointer("Cinematic Minimal Tense"),
                Previews:             []models.Preview{
                    models.Preview{
                        ContentType:          models.ToPointer(models.ContentTypeEnum_ENUMAUDIOMP3),
                        Url:                  models.ToPointer("https://public-cdn.ampermusic.com/bands/previews/cinematic_minimal_tense_band_1_v1.mp3"),
                    },
                    models.Preview{
                        ContentType:          models.ToPointer(models.ContentTypeEnum_ENUMAUDIOMP3),
                        Url:                  models.ToPointer("https://public-cdn.ampermusic.com/bands/previews/cinematic_minimal_tense_band_2_v1.mp3"),
                    },
                },
                Tags:                 []string{
                    "Tense",
                    "Cinematic",
                    "Negative",
                    "Simple Meter",
                    "4/4",
                    "Natural Minor",
                    "Dorian",
                    "Minimal",
                    "Adagio",
                    "Single Region",
                    "Main",
                    "Entertainment",
                    "Politics",
                    "Keys",
                    "Mid Pads",
                    "Fast",
                    "Slow",
                    "Slow",
                    "Voice",
                    "Medium Bright",
                    "Non Noisy",
                    "Medium Thick",
                    "Angelic",
                    "Direct",
                    "Percussion",
                    "Perc FX",
                    "Misc",
                    "Acoustic Pianos",
                    "Grand",
                    "Nice",
                    "Roomy",
                    "Pop",
                    "Upright",
                    "Clean",
                    "Classic",
                    "Keyboards",
                    "Digital Keyboard",
                    "Strings",
                    "Synth Basses",
                    "Fast",
                    "Dark",
                    "Thick",
                    "Sub",
                    "Synth Mallets",
                    "Dull",
                    "Mid Synth Beds",
                    "Slow",
                    "None",
                    "Medium Noisy",
                    "Harsh",
                    "Fast",
                    "Airy",
                    "Long Textures",
                    "Ambience",
                    "Synth Texture",
                    "Ethereal",
                    "Set Kicks",
                    "Processed",
                    "Hubcap Mallet",
                    "Wide",
                    "Tickie",
                    "Airy",
                    "Chamber",
                    "Thin",
                    "Organ",
                    "Cello Ensemble",
                    "Sweet",
                    "Big",
                    "Di",
                    "Raw",
                    "Bright",
                    "Tight",
                    "Chorus",
                    "Buzzy",
                    "Huge",
                    "Warm",
                    "Jazz",
                    "Brass",
                    "String",
                    "Hollow",
                    "Woodwind",
                    "Breathy",
                    "Crystal",
                    "Rhodes",
                    "Synth Piano",
                    "Noisy",
                    "Woody",
                    "Metallic",
                    "Reverse Piano",
                    "Full",
                    "Foley",
                    "Piano",
                    "Clean",
                    "Delayed",
                    "Reverb",
                    "Low Passed",
                    "Large",
                    "Medium",
                    "Small",
                },
            },
        },
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(1),
    }

}
```

