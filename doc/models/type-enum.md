
# Type Enum

The specific action to perform; if the event type is "ending" then this must be "ringout" and if event type is "transition" this must be "cut"

## Enumeration

`TypeEnum`

## Fields

| Name |
|  --- |
| `RINGOUT` |
| `CUT` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    mType := models.TypeEnum_RINGOUT

}
```

