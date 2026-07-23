
# License Format

Description of a license

## Structure

`LicenseFormat`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Description` | `*string` | Optional | Description of the license |
| `Format` | `*string` | Optional | Format or extension of the media, such as mpeg for videos or jpeg for images |
| `MediaType` | [`*models.MediaTypeEnum`](../../doc/models/media-type-enum.md) | Optional | Media type of the license |
| `MinResolution` | `*int` | Optional | Width of the media, in pixels, allowed by this license |
| `Size` | `*string` | Optional | Keyword that details the size of the media, such as hd or sd for video, huge or vector for images |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    licenseFormat := models.LicenseFormat{
        Description:          models.ToPointer("Med"),
        Format:               models.ToPointer("jpg"),
        MediaType:            models.ToPointer(models.MediaTypeEnum_IMAGE),
        MinResolution:        models.ToPointer(1000),
        Size:                 models.ToPointer("medium"),
    }

}
```

