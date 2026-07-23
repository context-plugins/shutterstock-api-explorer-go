
# Audio Asset Details

Information about a file that is part of an audio asset

## Structure

`AudioAssetDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `FileSize` | `*int` | Optional | File size of the track |
| `Url` | `*string` | Optional | URL the track is available at |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioAssetDetails := models.AudioAssetDetails{
        FileSize:             models.ToPointer(4453197),
        Url:                  models.ToPointer("https://ak.picdn.net/shutterstock/audio/442583/preview/preview.mp3"),
    }

}
```

