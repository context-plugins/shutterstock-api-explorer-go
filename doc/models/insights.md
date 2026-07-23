
# Insights

AI-powered insights about an asset, based on the specified audience and objective

## Structure

`Insights`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `LabelPerformance` | [`[]models.LabelPerformance`](../../doc/models/label-performance.md) | Required | How effective the AI thinks an asset in the category is for the specified audience and objective, expressed as a percentile compared to other images |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    insights := models.Insights{
        LabelPerformance:     []models.LabelPerformance{
            models.LabelPerformance{
                Name:                  models.ToPointer("Nature"),
                PercentilePerformance: models.ToPointer(float64(98.82123565673828)),
            },
            models.LabelPerformance{
                Name:                  models.ToPointer("Outdoors"),
                PercentilePerformance: models.ToPointer(float64(98.63294982910156)),
            },
        },
    }

}
```

