
# Commercial Status

## Structure

`CommercialStatus`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Reason` | `*string` | Optional | - |
| `Status` | `*string` | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    commercialStatus := models.CommercialStatus{
        Reason:               models.ToPointer("reason4"),
        Status:               models.ToPointer("status8"),
    }

}
```

