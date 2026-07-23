
# Create Audio Renders Request

Render request data

## Structure

`CreateAudioRendersRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AudioRenders` | [`[]models.CreateAudioRender`](../../doc/models/create-audio-render.md) | Required | Parameters to create computer audio renders |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    createAudioRendersRequest := models.CreateAudioRendersRequest{
        AudioRenders:         []models.CreateAudioRender{
            models.CreateAudioRender{
                Filename:             "My Project.mp3",
                Preset:               models.Preset1Enum_MASTERMP3,
                Timeline:             models.AudioRenderTimeline{
                    Spans:                []models.AudioRenderTimelineSpan{
                        models.AudioRenderTimelineSpan{
                            Id:                   models.ToPointer(float64(111)),
                            InstrumentGroups:     []models.AudioRenderTimelineSpanInstrumentGroup{
                                models.AudioRenderTimelineSpanInstrumentGroup{
                                    InstrumentGroup:      "roomy_kit",
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
                                    Tempo:                float64(86),
                                    Time:                 float64(5),
                                },
                            },
                            Time:                 5,
                        },
                        models.AudioRenderTimelineSpan{
                            Id:                   models.ToPointer(float64(114.48)),
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
                            },
                            Regions:              []models.AudioRenderTimelineSpanRegion{
                                models.AudioRenderTimelineSpanRegion{
                                    Beat:                 224,
                                    Descriptor:           "descriptor2",
                                    EndType:              models.ToPointer(models.EndType{
                                        Beat:                 float64(21.54),
                                        Event:                models.EventEnum_ENDING,
                                        Type:                 models.TypeEnum_RINGOUT,
                                    }),
                                    Id:                   float64(121.5),
                                    Key:                  models.ToPointer(models.Key{
                                        TonicAccidental:      models.ToPointer(models.TonicAccidentalEnum_FLAT),
                                        TonicNote:            models.ToPointer(models.TonicNoteEnum_C),
                                        TonicQuality:         models.ToPointer(models.TonicQualityEnum_LYDIAN),
                                    }),
                                    Region:               models.RegionEnum_MUSIC,
                                },
                                models.AudioRenderTimelineSpanRegion{
                                    Beat:                 224,
                                    Descriptor:           "descriptor2",
                                    EndType:              models.ToPointer(models.EndType{
                                        Beat:                 float64(21.54),
                                        Event:                models.EventEnum_ENDING,
                                        Type:                 models.TypeEnum_RINGOUT,
                                    }),
                                    Id:                   float64(121.5),
                                    Key:                  models.ToPointer(models.Key{
                                        TonicAccidental:      models.ToPointer(models.TonicAccidentalEnum_FLAT),
                                        TonicNote:            models.ToPointer(models.TonicNoteEnum_C),
                                        TonicQuality:         models.ToPointer(models.TonicQualityEnum_LYDIAN),
                                    }),
                                    Region:               models.RegionEnum_MUSIC,
                                },
                                models.AudioRenderTimelineSpanRegion{
                                    Beat:                 224,
                                    Descriptor:           "descriptor2",
                                    EndType:              models.ToPointer(models.EndType{
                                        Beat:                 float64(21.54),
                                        Event:                models.EventEnum_ENDING,
                                        Type:                 models.TypeEnum_RINGOUT,
                                    }),
                                    Id:                   float64(121.5),
                                    Key:                  models.ToPointer(models.Key{
                                        TonicAccidental:      models.ToPointer(models.TonicAccidentalEnum_FLAT),
                                        TonicNote:            models.ToPointer(models.TonicNoteEnum_C),
                                        TonicQuality:         models.ToPointer(models.TonicQualityEnum_LYDIAN),
                                    }),
                                    Region:               models.RegionEnum_MUSIC,
                                },
                            },
                            SpanType:             models.SpanTypeEnum_UNMETERED,
                            Tempo:                models.ToPointer(14),
                            TempoChanges:         []models.AudioRenderTimelineSpanTempoChanges{
                                models.AudioRenderTimelineSpanTempoChanges{
                                    Tempo:                float64(108.32),
                                    Time:                 float64(39.44),
                                },
                            },
                            Time:                 20,
                        },
                    },
                },
            },
        },
    }

}
```

