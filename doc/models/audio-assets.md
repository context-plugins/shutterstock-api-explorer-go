
# Audio Assets

Files that are available as part of an audio asset

## Structure

`AudioAssets`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AlbumArt` | [`*models.AudioAssetDetails`](../../doc/models/audio-asset-details.md) | Optional | Information about a file that is part of an audio asset |
| `CleanAudio` | [`*models.AudioAssetDetails`](../../doc/models/audio-asset-details.md) | Optional | Information about a file that is part of an audio asset |
| `OriginalAudio` | [`*models.AudioAssetDetails`](../../doc/models/audio-asset-details.md) | Optional | Information about a file that is part of an audio asset |
| `PreviewMp3` | [`*models.AudioAssetDetails`](../../doc/models/audio-asset-details.md) | Optional | Information about a file that is part of an audio asset |
| `PreviewOgg` | [`*models.AudioAssetDetails`](../../doc/models/audio-asset-details.md) | Optional | Information about a file that is part of an audio asset |
| `ShortsLoopsStems` | [`*models.ShortsLoopsStems`](../../doc/models/shorts-loops-stems.md) | Optional | Links for Shorts, Loops and Stems previews |
| `Waveform` | [`*models.AudioAssetDetails`](../../doc/models/audio-asset-details.md) | Optional | Information about a file that is part of an audio asset |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioAssets := models.AudioAssets{
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
    }

}
```

