
# Audio Render Timeline Span Instrument Group

An instrument and the status objects that specify when that instrument plays

## Structure

`AudioRenderTimelineSpanInstrumentGroup`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `InstrumentGroup` | `string` | Required | The instrument ID |
| `Statuses` | [`[]models.AudioRenderTimelineSpanInstrumentGroupStatus`](../../doc/models/audio-render-timeline-span-instrument-group-status.md) | Optional | An array of status objects |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    audioRenderTimelineSpanInstrumentGroup := models.AudioRenderTimelineSpanInstrumentGroup{
        InstrumentGroup:      "bright_roomy_kit",
        Statuses:             []models.AudioRenderTimelineSpanInstrumentGroupStatus{
            models.AudioRenderTimelineSpanInstrumentGroupStatus{
                Beat:                 float64(12),
                Status:               models.Status1Enum_ACTIVE,
            },
        },
    }

}
```

