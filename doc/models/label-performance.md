
# Label Performance

## Structure

`LabelPerformance`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Name` | `*string` | Optional | - |
| `PercentilePerformance` | `*float64` | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    labelPerformance := models.LabelPerformance{
        Name:                  models.ToPointer("name0"),
        PercentilePerformance: models.ToPointer(float64(191.04)),
    }

}
```

