
# Status Enum

A coarse progress indicator

## Enumeration

`StatusEnum`

## Fields

| Name |
|  --- |
| `WAITINGCOMPOSE` |
| `RUNNINGCOMPOSE` |
| `WAITINGRENDER` |
| `RUNNINGRENDER` |
| `CREATED` |
| `FAILEDCREATE` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    status := models.StatusEnum_WAITINGRENDER

}
```

