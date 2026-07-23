
# Catalog Collection Role

A user that has access to a catalog collection

## Structure

`CatalogCollectionRole`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Email` | `string` | Required | - |
| `Id` | `string` | Required | - |
| `Type` | `string` | Required, Constant | **Value**: `"USER"` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    catalogCollectionRole := models.CatalogCollectionRole{
        Email:                "user123@org.com",
        Id:                   "123",
        Type:                 "USER",
    }

}
```

