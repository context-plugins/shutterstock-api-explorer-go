
# End Type

A high-level description of how a region ends

## Structure

`EndType`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Beat` | `float64` | Required | The beat, relative to the start of the active region, at which the end_type begins; in other words, the ending starts on this beat of the region |
| `Event` | [`models.EventEnum`](../../doc/models/event-enum.md) | Required | The type of event |
| `Type` | [`models.TypeEnum`](../../doc/models/type-enum.md) | Required | The specific action to perform; if the event type is "ending" then this must be "ringout" and if event type is "transition" this must be "cut" |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    endType := models.EndType{
        Beat:                 float64(249),
        Event:                models.EventEnum_ENDING,
        Type:                 models.TypeEnum_RINGOUT,
    }

}
```

