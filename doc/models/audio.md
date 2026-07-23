
# Audio

Audio metadata

## Structure

`Audio`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AddedDate` | `*time.Time` | Optional | Date this track was added to the Shutterstock library |
| `AffiliateUrl` | `*string` | Optional | Affiliate referral link; appears only for registered affiliate partners |
| `Album` | [`*models.Album`](../../doc/models/album.md) | Optional | Album metadata |
| `Artists` | [`[]models.Artist`](../../doc/models/artist.md) | Optional | List of artists |
| `Assets` | [`*models.AudioAssets`](../../doc/models/audio-assets.md) | Optional | Files that are available as part of an audio asset |
| `Bpm` | `*int` | Optional | BPM (beats per minute) of this track |
| `Contributor` | [`models.Contributor`](../../doc/models/contributor.md) | Required | Information about a contributor |
| `DeletedTime` | `*time.Time` | Optional | - |
| `Description` | `*string` | Optional | Description of this track |
| `Duration` | `*float64` | Optional | Duration of this track in seconds |
| `Genres` | `[]string` | Optional | List of all genres for this track |
| `Id` | `string` | Required | Shutterstock ID of this track |
| `Instruments` | `[]string` | Optional | List of all instruments that appear in this track |
| `IsAdult` | `*bool` | Optional | Whether or not this track contains adult content |
| `IsInstrumental` | `*bool` | Optional | Whether or not this track is purely instrumental (lacking lyrics) |
| `Isrc` | `*string` | Optional | - |
| `Keywords` | `[]string` | Optional | List of all keywords for this track |
| `Language` | `*string` | Optional | Language of this track's lyrics |
| `Lyrics` | `*string` | Optional | Lyrics of this track |
| `MediaType` | `string` | Required | Media type of this track; should always be "audio" |
| `ModelReleases` | [`[]models.ModelRelease`](../../doc/models/model-release.md) | Optional | List of all model releases for this track |
| `Moods` | `[]string` | Optional | List of all moods of this track |
| `PublishedTime` | `*time.Time` | Optional | Time this track was published |
| `RecordingVersion` | `*string` | Optional | Recording version of this track |
| `Releases` | `[]string` | Optional | List of all releases of this track |
| `SimilarArtists` | [`[]models.Artist`](../../doc/models/artist.md) | Optional | List of all similar artists of this track |
| `SubmittedTime` | `*time.Time` | Optional | Time this track was submitted |
| `Title` | `*string` | Optional | Title of this track |
| `UpdatedTime` | `*time.Time` | Optional | Time this track was last updated |
| `Url` | `*string` | Optional | - |
| `VocalDescription` | `*string` | Optional | Vocal description of this track |

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
    audio := models.Audio{
        AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-08-16", func(err error) { log.Fatalln(err) })),
        AffiliateUrl:         models.ToPointer("affiliate_url4"),
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
    }

}
```

