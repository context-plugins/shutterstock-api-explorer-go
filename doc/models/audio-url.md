
# Audio Url

Audio License URL object

## Structure

`AudioUrl`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ShortsLoopsStems` | `*string` | Optional | URL that can be used to download the .zip file containing shorts, loops, and stems |
| `Url` | `string` | Required | URL that can be used to download the unwatermarked, licensed asset |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioUrl := models.AudioUrl{
        ShortsLoopsStems:     models.ToPointer("shorts_loops_stems2"),
        Url:                  "url6",
    }

}
```

