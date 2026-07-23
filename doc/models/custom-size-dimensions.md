
# Custom Size Dimensions

A custom height or a custom width to resize the image to, but not both (experimental)

## Structure

`CustomSizeDimensions`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Height` | `*int` | Optional | Custom height to resize the image to<br><br>**Constraints**: `>= 100` |
| `Width` | `*int` | Optional | Custom width to resize the image to<br><br>**Constraints**: `>= 100` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    customSizeDimensions := models.CustomSizeDimensions{
        Height:               models.ToPointer(600),
        Width:                models.ToPointer(800),
    }

}
```

