
# Audio Render Timeline Span Tempo Changes

An inflection point in a tempo curve; the API creates the overall tempo by using a linear interpolation of the time between each tempo change

## Structure

`AudioRenderTimelineSpanTempoChanges`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Tempo` | `float64` | Required | The tempo, in beats per minute, active at this time |
| `Time` | `float64` | Required | The time, in seconds, at which the tempo exists |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioRenderTimelineSpanTempoChanges := models.AudioRenderTimelineSpanTempoChanges{
        Tempo:                float64(86),
        Time:                 float64(5),
    }

}
```

