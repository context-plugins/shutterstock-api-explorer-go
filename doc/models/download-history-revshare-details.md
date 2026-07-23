
# Download History Revshare Details

Pricing information for revenue-sharing transactions

## Structure

`DownloadHistoryRevshareDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `PurchaseAmount` | `string` | Required | The amount charged for the license |
| `PurchaseCurrency` | `string` | Required | The currency the amount was charged in |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    downloadHistoryRevshareDetails := models.DownloadHistoryRevshareDetails{
        PurchaseAmount:       "8.65",
        PurchaseCurrency:     "USD",
    }

}
```

