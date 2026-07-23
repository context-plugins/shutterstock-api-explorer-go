
# Audio Render Timeline Span

The beginning of a non-overlapping period of absolute time

## Structure

`AudioRenderTimelineSpan`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*float64` | Optional | An identifier which must be unique within the parent span |
| `InstrumentGroups` | [`[]models.AudioRenderTimelineSpanInstrumentGroup`](../../doc/models/audio-render-timeline-span-instrument-group.md) | Optional | An array of instrument_group objects that are used in this span |
| `Regions` | [`[]models.AudioRenderTimelineSpanRegion`](../../doc/models/audio-render-timeline-span-region.md) | Optional | An array of region objects within the span |
| `SpanType` | [`models.SpanTypeEnum`](../../doc/models/span-type-enum.md) | Required | Type of span; metered spans represent a pariod of time with music, and unmetered spans denote the end of the prior metered span |
| `Tempo` | `*int` | Optional | The tempo, in beats per minute, at the start of the span; if not provided, the API selects a random tempo |
| `TempoChanges` | [`[]models.AudioRenderTimelineSpanTempoChanges`](../../doc/models/audio-render-timeline-span-tempo-changes.md) | Optional | Two or more inflection points in a tempo curve; the API creates a smoothly changing tempo by using a linear interpolation of the time between each tempo change |
| `Time` | `int` | Required | The absolute time, in seconds, at which the span starts |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioRenderTimelineSpan := models.AudioRenderTimelineSpan{
        Id:                   models.ToPointer(float64(111)),
        InstrumentGroups:     []models.AudioRenderTimelineSpanInstrumentGroup{
            models.AudioRenderTimelineSpanInstrumentGroup{
                InstrumentGroup:      "instrument_group0",
                Statuses:             []models.AudioRenderTimelineSpanInstrumentGroupStatus{
                    models.AudioRenderTimelineSpanInstrumentGroupStatus{
                        Beat:                 float64(41.62),
                        Status:               models.Status1Enum_ACTIVE,
                    },
                    models.AudioRenderTimelineSpanInstrumentGroupStatus{
                        Beat:                 float64(41.62),
                        Status:               models.Status1Enum_ACTIVE,
                    },
                },
            },
            models.AudioRenderTimelineSpanInstrumentGroup{
                InstrumentGroup:      "instrument_group0",
                Statuses:             []models.AudioRenderTimelineSpanInstrumentGroupStatus{
                    models.AudioRenderTimelineSpanInstrumentGroupStatus{
                        Beat:                 float64(41.62),
                        Status:               models.Status1Enum_ACTIVE,
                    },
                    models.AudioRenderTimelineSpanInstrumentGroupStatus{
                        Beat:                 float64(41.62),
                        Status:               models.Status1Enum_ACTIVE,
                    },
                },
            },
            models.AudioRenderTimelineSpanInstrumentGroup{
                InstrumentGroup:      "instrument_group0",
                Statuses:             []models.AudioRenderTimelineSpanInstrumentGroupStatus{
                    models.AudioRenderTimelineSpanInstrumentGroupStatus{
                        Beat:                 float64(41.62),
                        Status:               models.Status1Enum_ACTIVE,
                    },
                    models.AudioRenderTimelineSpanInstrumentGroupStatus{
                        Beat:                 float64(41.62),
                        Status:               models.Status1Enum_ACTIVE,
                    },
                },
            },
        },
        Regions:              []models.AudioRenderTimelineSpanRegion{
            models.AudioRenderTimelineSpanRegion{
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
            },
        },
        SpanType:             models.SpanTypeEnum_METERED,
        Tempo:                models.ToPointer(76),
        TempoChanges:         []models.AudioRenderTimelineSpanTempoChanges{
            models.AudioRenderTimelineSpanTempoChanges{
                Tempo:                float64(108.32),
                Time:                 float64(39.44),
            },
            models.AudioRenderTimelineSpanTempoChanges{
                Tempo:                float64(108.32),
                Time:                 float64(39.44),
            },
        },
        Time:                 0,
    }

}
```

