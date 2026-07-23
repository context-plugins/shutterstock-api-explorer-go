
# Video Size Details

Video asset information

## Structure

`VideoSizeDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `DisplayName` | `*string` | Optional | Display name of this video size |
| `FileSize` | `*int` | Optional | File size (in bytes) of this video size |
| `Format` | `*string` | Optional | Format of this video size |
| `Fps` | `*float64` | Optional | Frames per second of this video size |
| `Height` | `*int` | Optional | Height of this video size |
| `IsLicensable` | `*bool` | Optional | Whether or not videos can be licensed in this video size |
| `Width` | `*int` | Optional | Width of this video size |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    videoSizeDetails := models.VideoSizeDetails{
        DisplayName:          models.ToPointer("Original HD"),
        FileSize:             models.ToPointer(110359552),
        Format:               models.ToPointer("avc1"),
        Fps:                  models.ToPointer(float64(29.97)),
        Height:               models.ToPointer(1080),
        IsLicensable:         models.ToPointer(true),
        Width:                models.ToPointer(1920),
    }

}
```

