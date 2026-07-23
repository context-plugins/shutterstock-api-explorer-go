
# Audio Renders Files List

Files associated with the render

## Structure

`AudioRendersFilesList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `BitsSample` | `float64` | Required | The bit depth of the audio files in bits/sample |
| `ContentType` | `string` | Required | The content-type of the file |
| `DownloadUrl` | `string` | Required | The internet-accessible URL from which the file can be downloaded. Any redirects encountered when using this URL must be followed |
| `Filename` | `string` | Required | The user-specified file name suggestion from the render request; this file name becomes the filename property of the Content-Disposition header when the user downloads the rendered audio file |
| `FrequencyHz` | `float64` | Required | The Sample rate of the audio files in Hertz (Hz) |
| `KbitsSecond` | `float64` | Required | The data rate of the audio files in kilobits/second |
| `SizeBytes` | `float64` | Required | Size of the file in bytes |
| `Tracks` | `[]string` | Required | An array of track names included in the file |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioRendersFilesList := models.AudioRendersFilesList{
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
    }

}
```

