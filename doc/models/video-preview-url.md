
# Video Preview Url

Video preview information

## Structure

`VideoPreviewUrl`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Url` | `string` | Required | Direct URL to the image |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    videoPreviewUrl := models.VideoPreviewUrl{
        Url:                  "https://ak.picdn.net/shutterstock/videos/1033184651/thumb/stock-footage-camera-follows-hipster-millennial-young-woman-in-orange-jacket-running-up-on-top-of-mountain-summit.mp4",
    }

}
```

