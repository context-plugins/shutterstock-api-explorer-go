
# Audio Data List

List of tracks

## Structure

`AudioDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Audio`](../../doc/models/audio.md) | Optional | Tracks |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |
| `TotalCount` | `*int` | Optional | Total count of all results across all pages |

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
    audioDataList := models.AudioDataList{
        Data:                 []models.Audio{
            models.Audio{
                AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-04-12", func(err error) { log.Fatalln(err) })),
                AffiliateUrl:         models.ToPointer("affiliate_url6"),
                Album:                nil,
                Artists:              []models.Artist{
                    models.Artist{
                        Name:                 "Fin Productions",
                    },
                },
                Assets:               models.ToPointer(models.AudioAssets{
                    AlbumArt:             nil,
                    CleanAudio:           models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(30760372),
                        Url:                  models.ToPointer("url4"),
                    }),
                    OriginalAudio:        nil,
                    PreviewMp3:           models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(3846606),
                        Url:                  models.ToPointer("https://ak.picdn.net/shutterstock/audio/434750/preview/preview.mp3"),
                    }),
                    PreviewOgg:           models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(4402608),
                        Url:                  models.ToPointer("https://ak.picdn.net/shutterstock/audio/434750/preview/preview.ogg"),
                    }),
                    Waveform:             models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(19822),
                        Url:                  models.ToPointer("https://ak.picdn.net/shutterstock/audio/434750/waveform/waveform.png"),
                    }),
                }),
                Bpm:                  models.ToPointer(100),
                Contributor:          models.Contributor{
                    Id:                   "2847971",
                },
                Description:          models.ToPointer("Pulsing and feel-good, featuring slick electric guitar, synthesizer, bass, electronic drum pads and drums that create a positive, celebratory mood."),
                Duration:             models.ToPointer(float64(160)),
                Genres:               []string{
                    "Dance/Electronic",
                    "Electro Pop",
                    "Pop/Rock",
                },
                Id:                   "434750",
                Instruments:          []string{
                    "Bass",
                    "Drums",
                    "Electric guitar",
                    "Pads",
                    "Percussion",
                    "Synthesizer",
                },
                IsAdult:              models.ToPointer(false),
                IsInstrumental:       models.ToPointer(true),
                Isrc:                 models.ToPointer(""),
                Keywords:             []string{
                    "breezy",
                    "celebration",
                    "festive",
                    "good times",
                    "hopeful",
                    "optimistic",
                    "party",
                    "positive",
                    "reflective",
                },
                Language:             models.ToPointer("en"),
                Lyrics:               models.ToPointer(""),
                MediaType:            "audio",
                Moods:                []string{
                    "Bright",
                    "Confident",
                    "Fun",
                    "Happy",
                    "Inspiring",
                    "Optimistic",
                    "Playful",
                    "Sophisticated",
                    "Stylish",
                    "Uplifting",
                },
                PublishedTime:        models.ToPointer(parseTime(time.RFC3339, "2016-04-12T17:45:29-04:00", func(err error) { log.Fatalln(err) })),
                RecordingVersion:     models.ToPointer(""),
                Releases:             []string{
                },
                SimilarArtists:       []models.Artist{
                },
                Title:                models.ToPointer("Fresh Love"),
                UpdatedTime:          models.ToPointer(parseTime(time.RFC3339, "2016-08-18T18:03:11-04:00", func(err error) { log.Fatalln(err) })),
                VocalDescription:     models.ToPointer(""),
            },
        },
        Errors:               []models.Error{
            models.Error{
                Code:                 models.ToPointer("code8"),
                Data:                 models.ToPointer("data0"),
                Items:                []interface{}{
                    interface{}("[key1, val1][key2, val2]"),
                },
                Message:              "message0",
                Path:                 models.ToPointer("path4"),
            },
            models.Error{
                Code:                 models.ToPointer("code8"),
                Data:                 models.ToPointer("data0"),
                Items:                []interface{}{
                    interface{}("[key1, val1][key2, val2]"),
                },
                Message:              "message0",
                Path:                 models.ToPointer("path4"),
            },
            models.Error{
                Code:                 models.ToPointer("code8"),
                Data:                 models.ToPointer("data0"),
                Items:                []interface{}{
                    interface{}("[key1, val1][key2, val2]"),
                },
                Message:              "message0",
                Path:                 models.ToPointer("path4"),
            },
        },
        Message:              models.ToPointer("message4"),
        Page:                 models.ToPointer(76),
        PerPage:              models.ToPointer(244),
    }

}
```

