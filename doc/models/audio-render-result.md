
# Audio Render Result

The output of an audio render in WAV or MP3 format

## Structure

`AudioRenderResult`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CreatedDate` | `*time.Time` | Optional | The time the render was submitted to the API |
| `Files` | [`[]models.AudioRendersFilesList`](../../doc/models/audio-renders-files-list.md) | Optional | The files associated with the render |
| `Id` | `string` | Required | The alphanumeric ID of the simple render |
| `Preset` | [`*models.PresetEnum`](../../doc/models/preset-enum.md) | Optional | The file format preset |
| `ProgressPercent` | `*int` | Optional | The current progress of the render as a percentage |
| `Status` | [`models.StatusEnum`](../../doc/models/status-enum.md) | Required | A coarse progress indicator |
| `Timeline` | [`models.AudioRenderTimeline`](../../doc/models/audio-render-timeline.md) | Required | A timeline object that represents either a request for music to be created or an entire music composition |
| `UpdatedDate` | `*time.Time` | Optional | The time that the audio output was uploaded |

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
    audioRenderResult := models.AudioRenderResult{
        CreatedDate:          models.ToPointer(parseTime(time.RFC3339, "2021-07-13T16:19:30-04:00", func(err error) { log.Fatalln(err) })),
        Files:                []models.AudioRendersFilesList{
        },
        Id:                   "2yZp13IhLqnjfh2KquDTOHUHzTiP",
        Preset:               models.ToPointer(models.PresetEnum_MASTERMP3),
        ProgressPercent:      models.ToPointer(0),
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
    }

}
```

