
# Audio Render Timeline Span Region

A period of music or silence, measured in beats

## Structure

`AudioRenderTimelineSpanRegion`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Beat` | `int` | Required | The beat, relative to the span, at which the region object's music begins |
| `Descriptor` | `string` | Required | The descriptor ID needed to compose the music |
| `EndType` | [`*models.EndType`](../../doc/models/end-type.md) | Optional | A high-level description of how a region ends |
| `Id` | `float64` | Required | An identifier which must be unique within the parent span |
| `Key` | [`*models.Key`](../../doc/models/key.md) | Optional | The key signature active at the beginning of the region |
| `Region` | [`models.RegionEnum`](../../doc/models/region-enum.md) | Required | The type of region |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioRenderTimelineSpanRegion := models.AudioRenderTimelineSpanRegion{
        Beat:                 12,
        Descriptor:           "cinematic_minimal_tense",
        EndType:              models.ToPointer(models.EndType{
            Beat:                 float64(24),
            Event:                models.EventEnum_ENDING,
            Type:                 models.TypeEnum_RINGOUT,
        }),
        Id:                   float64(222),
        Key:                  models.ToPointer(models.Key{
            TonicAccidental:      models.ToPointer(models.TonicAccidentalEnum_FLAT),
            TonicNote:            models.ToPointer(models.TonicNoteEnum_C),
            TonicQuality:         models.ToPointer(models.TonicQualityEnum_MAJOR),
        }),
        Region:               models.RegionEnum_MUSIC,
    }

}
```

