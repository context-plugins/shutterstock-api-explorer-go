
# Shorts Loops Stems

Links for Shorts, Loops and Stems previews

## Structure

`ShortsLoopsStems`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Loops` | [`map[string]models.Loops`](../../doc/models/loops.md) | Optional | - |
| `Shorts` | [`map[string]models.Shorts`](../../doc/models/shorts.md) | Optional | - |
| `Stems` | [`map[string]models.Stems`](../../doc/models/stems.md) | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    shortsLoopsStems := models.ShortsLoopsStems{
        Loops:                map[string]models.Loops{
            "loop_preview_1": models.Loops{
                Url:                  models.ToPointer("http://picdn.shuttercorp.net/shutterstock/audio/464947/loop_preview_1/loop_preview_1.mp3"),
            },
            "loop_preview_2": models.Loops{
                Url:                  models.ToPointer("http://picdn.shuttercorp.net/shutterstock/audio/464947/loop_preview_2/loop_preview_2.mp3"),
            },
        },
        Shorts:               map[string]models.Shorts{
            "short_preview_1": models.Shorts{
                Url:                  models.ToPointer("http://picdn.shuttercorp.net/shutterstock/audio/464947/short_preview_1/short_preview_1.mp3"),
            },
            "short_preview_2": models.Shorts{
                Url:                  models.ToPointer("http://picdn.shuttercorp.net/shutterstock/audio/464947/short_preview_2/short_preview_2.mp3"),
            },
        },
        Stems:                map[string]models.Stems{
            "stem_preview_1": models.Stems{
                Url:                  models.ToPointer("http://picdn.shuttercorp.net/shutterstock/audio/464947/stem_preview_1/stem_preview_1.mp3"),
            },
            "stem_preview_2": models.Stems{
                Url:                  models.ToPointer("http://picdn.shuttercorp.net/shutterstock/audio/464947/stem_preview_1/stem_preview_1.mp3"),
            },
        },
    }

}
```

