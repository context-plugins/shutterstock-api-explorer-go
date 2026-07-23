
# Audio Search Results

Audio search results

## Structure

`AudioSearchResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.Audio`](../../doc/models/audio.md) | Required | List of tracks |
| `Message` | `*string` | Optional | Server-generated message, if any |
| `Page` | `*int` | Optional | Current page that is returned |
| `PerPage` | `*int` | Optional | Number of results per page |
| `SearchId` | `string` | Required | ID of the search |
| `TotalCount` | `int` | Required | Total count of all results across all pages |

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
    audioSearchResults := models.AudioSearchResults{
        Data:                 []models.Audio{
            models.Audio{
                AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-08-16", func(err error) { log.Fatalln(err) })),
                AffiliateUrl:         models.ToPointer("affiliate_url6"),
                Album:                nil,
                Artists:              []models.Artist{
                    models.Artist{
                        Name:                 "Klimenko Music",
                    },
                },
                Assets:               models.ToPointer(models.AudioAssets{
                    AlbumArt:             nil,
                    CleanAudio:           models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(35188408),
                        Url:                  models.ToPointer("url4"),
                    }),
                    OriginalAudio:        nil,
                    PreviewMp3:           models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(4400203),
                        Url:                  models.ToPointer("https://ak.picdn.net/shutterstock/audio/442583/preview/preview.mp3"),
                    }),
                    PreviewOgg:           models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(4453197),
                        Url:                  models.ToPointer("https://ak.picdn.net/shutterstock/audio/442583/preview/preview.ogg"),
                    }),
                    Waveform:             models.ToPointer(models.AudioAssetDetails{
                        FileSize:             models.ToPointer(18778),
                        Url:                  models.ToPointer("https://ak.picdn.net/shutterstock/audio/442583/waveform/waveform.png"),
                    }),
                }),
                Bpm:                  models.ToPointer(110),
                Contributor:          models.Contributor{
                    Id:                   "2847971",
                },
                Description:          models.ToPointer("Pulsing and feel-good, featuring soaring synthesizer, groovy synth bass drums and synth drums that create a euphoric, upbeat mood."),
                Duration:             models.ToPointer(float64(183)),
                Genres:               []string{
                    "Dance/Electronic",
                    "Electro Pop",
                    "Pop/Rock",
                },
                Id:                   "442583",
                Instruments:          []string{
                    "Piano",
                    "Synth bass",
                    "Synth drums",
                    "Synthesizer",
                },
                IsAdult:              models.ToPointer(false),
                IsInstrumental:       models.ToPointer(true),
                Isrc:                 models.ToPointer(""),
                Keywords:             []string{
                    "celebratory",
                    "chic",
                    "euphoric",
                    "good times",
                    "hip",
                    "optimistic",
                    "party",
                    "soaring",
                    "upbeat",
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
                PublishedTime:        models.ToPointer(parseTime(time.RFC3339, "2016-08-16T14:30:03-04:00", func(err error) { log.Fatalln(err) })),
                RecordingVersion:     models.ToPointer(""),
                Releases:             []string{
                },
                SimilarArtists:       []models.Artist{
                },
                Title:                models.ToPointer("Another Tomorrow"),
                UpdatedTime:          models.ToPointer(parseTime(time.RFC3339, "2016-08-18T17:59:33-04:00", func(err error) { log.Fatalln(err) })),
                Url:                  models.ToPointer(""),
                VocalDescription:     models.ToPointer(""),
            },
        },
        Message:              models.ToPointer("message2"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(5),
        SearchId:             "749090bb-2967-4a20-b22e-c800dc845e10",
        TotalCount:           123455,
    }

}
```

