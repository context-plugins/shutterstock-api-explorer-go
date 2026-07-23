
# Price

Price

## Structure

`Price`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `LocalAmount` | `*float64` | Optional | Floating-point amount of the calculated rev-share price in the currency local_currency |
| `LocalCurrency` | `*string` | Optional | Currency of the rev-share price that was calculated |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    price := models.Price{
        LocalAmount:          models.ToPointer(float64(12.34)),
        LocalCurrency:        models.ToPointer("EUR"),
    }

}
```

