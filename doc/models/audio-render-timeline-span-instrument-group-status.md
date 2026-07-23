
# Audio Render Timeline Span Instrument Group Status

The status of an instrument at a specific beat

## Structure

`AudioRenderTimelineSpanInstrumentGroupStatus`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Beat` | `float64` | Required | The beat, relative to the span, at which the status begins |
| `Status` | [`models.Status1Enum`](../../doc/models/status-1-enum.md) | Required | Whether the instrument is playing or not |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioRenderTimelineSpanInstrumentGroupStatus := models.AudioRenderTimelineSpanInstrumentGroupStatus{
        Beat:                 float64(12),
        Status:               models.Status1Enum_ACTIVE,
    }

}
```

