
# Image Size Details

Image size information

## Structure

`ImageSizeDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `DisplayName` | `*string` | Optional | Display name of this image size |
| `Dpi` | `*int` | Optional | - |
| `FileSize` | `*int` | Optional | File size (in bytes) of this image size |
| `Format` | `*string` | Optional | Format of this image size |
| `Height` | `*int` | Optional | Height of this image size |
| `IsLicensable` | `*bool` | Optional | Whether or not this image can be licensed in this image size |
| `Width` | `*int` | Optional | Width of this image size |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    imageSizeDetails := models.ImageSizeDetails{
        DisplayName:          models.ToPointer("Med"),
        Dpi:                  models.ToPointer(300),
        FileSize:             models.ToPointer(860200),
        Format:               models.ToPointer("jpg"),
        Height:               models.ToPointer(667),
        IsLicensable:         models.ToPointer(true),
        Width:                models.ToPointer(1000),
    }

}
```

