
# Audio Render Timeline

A timeline object that represents either a request for music to be created or an entire music composition

## Structure

`AudioRenderTimeline`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Spans` | [`[]models.AudioRenderTimelineSpan`](../../doc/models/audio-render-timeline-span.md) | Optional | A span object that represents the beginning of a period of absolute time |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioRenderTimeline := models.AudioRenderTimeline{
        Spans:                []models.AudioRenderTimelineSpan{
            models.AudioRenderTimelineSpan{
                Id:                   models.ToPointer(float64(123456)),
                InstrumentGroups:     []models.AudioRenderTimelineSpanInstrumentGroup{
                    models.AudioRenderTimelineSpanInstrumentGroup{
                        InstrumentGroup:      "The instrument ID",
                        Statuses:             []models.AudioRenderTimelineSpanInstrumentGroupStatus{
                            models.AudioRenderTimelineSpanInstrumentGroupStatus{
                                Beat:                 float64(12),
                                Status:               models.Status1Enum_ACTIVE,
                            },
                        },
                    },
                },
                Regions:              []models.AudioRenderTimelineSpanRegion{
                    models.AudioRenderTimelineSpanRegion{
                        Beat:                 12,
                        Descriptor:           "The descriptor ID needed to compose the music",
                        EndType:              models.ToPointer(models.EndType{
                            Beat:                 float64(12),
                            Event:                models.EventEnum_ENDING,
                            Type:                 models.TypeEnum_RINGOUT,
                        }),
                        Id:                   float64(123456),
                        Key:                  models.ToPointer(models.Key{
                            TonicAccidental:      models.ToPointer(models.TonicAccidentalEnum_ENUMDOUBLEFLAT),
                            TonicNote:            models.ToPointer(models.TonicNoteEnum_C),
                            TonicQuality:         models.ToPointer(models.TonicQualityEnum_MAJOR),
                        }),
                        Region:               models.RegionEnum_MUSIC,
                    },
                },
                SpanType:             models.SpanTypeEnum_METERED,
                Tempo:                models.ToPointer(12345),
                TempoChanges:         []models.AudioRenderTimelineSpanTempoChanges{
                    models.AudioRenderTimelineSpanTempoChanges{
                        Tempo:                float64(12345),
                        Time:                 float64(5),
                    },
                },
                Time:                 5,
            },
        },
    }

}
```

