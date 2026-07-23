
# Audio Renders List Results

Audio render data

## Structure

`AudioRendersListResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AudioRenders` | [`[]models.AudioRenderResult`](../../doc/models/audio-render-result.md) | Required | Audio render results |

## Example

```go
package main

import (
    "log"
    "time"
    "shutterstockapiexplorer/models"
)

func main() {
    parseTime := func(layout, value string, errCallback func(error)) time.Time {
        dateTime, err := time.Parse(layout, value)
        if err != nil {
            errCallback(err) 
       }
        return dateTime
    }
    audioRendersListResults := models.AudioRendersListResults{
        AudioRenders:         []models.AudioRenderResult{
            models.AudioRenderResult{
                CreatedDate:          models.ToPointer(parseTime(time.RFC3339, "2021-07-13T16:19:30-04:00", func(err error) { log.Fatalln(err) })),
                Files:                []models.AudioRendersFilesList{
                },
                Id:                   "2yZp13IhLqnjfh2KquDTOHUHzTiP",
                Preset:               models.ToPointer(models.PresetEnum_MASTERMP3),
                ProgressPercent:      models.ToPointer(20),
                Status:               models.StatusEnum_WAITINGCOMPOSE,
                Timeline:             models.AudioRenderTimeline{
                    Spans:                []models.AudioRenderTimelineSpan{
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
                            SpanType:             models.SpanTypeEnum_METERED,
                            Tempo:                models.ToPointer(14),
                            TempoChanges:         []models.AudioRenderTimelineSpanTempoChanges{
                                models.AudioRenderTimelineSpanTempoChanges{
                                    Tempo:                float64(108.32),
                                    Time:                 float64(39.44),
                                },
                            },
                            Time:                 86,
                        },
                    },
                },
                UpdatedDate:          models.ToPointer(parseTime(time.RFC3339, "2021-07-13T16:19:30-04:00", func(err error) { log.Fatalln(err) })),
            },
            models.AudioRenderResult{
                CreatedDate:          models.ToPointer(parseTime(time.RFC3339, "2021-07-12T16:39:59-04:00", func(err error) { log.Fatalln(err) })),
                Files:                []models.AudioRendersFilesList{
                    models.AudioRendersFilesList{
                        BitsSample:           float64(16),
                        ContentType:          "audio/mp3",
                        DownloadUrl:          "https://s3.amazonaws.com/prod-amper-inferno-ephemeral/renders/2021/07/13/amper-api-QwAgKqXQAzr622KuXYZ25C9WRH3a/0.mp3",
                        Filename:             "My_audio_ai.mp3",
                        FrequencyHz:          float64(44100),
                        KbitsSecond:          float64(192),
                        SizeBytes:            float64(481556),
                        Tracks:               []string{
                            "master",
                        },
                    },
                    models.AudioRendersFilesList{
                        BitsSample:           float64(0),
                        ContentType:          "application/vnd.amper.waveform+json",
                        DownloadUrl:          "https://s3.amazonaws.com/prod-amper-inferno-ephemeral/renders/2021/07/13/amper-api-QwAgKqXQAzr622KuXYZ25C9WRH3a/1.json",
                        Filename:             "render.json",
                        FrequencyHz:          float64(42),
                        KbitsSecond:          float64(0),
                        SizeBytes:            float64(4420),
                        Tracks:               []string{
                            "master",
                        },
                    },
                },
                Id:                   "QwAgKqXQAzr622KuXYZ25C9WRH3a",
                Preset:               models.ToPointer(models.PresetEnum_MASTERMP3),
                ProgressPercent:      models.ToPointer(100),
                Status:               models.StatusEnum_CREATED,
                Timeline:             models.AudioRenderTimeline{
                    Spans:                []models.AudioRenderTimelineSpan{
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
                            SpanType:             models.SpanTypeEnum_METERED,
                            Tempo:                models.ToPointer(14),
                            TempoChanges:         []models.AudioRenderTimelineSpanTempoChanges{
                                models.AudioRenderTimelineSpanTempoChanges{
                                    Tempo:                float64(108.32),
                                    Time:                 float64(39.44),
                                },
                            },
                            Time:                 86,
                        },
                    },
                },
                UpdatedDate:          models.ToPointer(parseTime(time.RFC3339, "2021-07-12T16:46:26-04:00", func(err error) { log.Fatalln(err) })),
            },
        },
    }

}
```

