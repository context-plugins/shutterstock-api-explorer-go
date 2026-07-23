
# Create Catalog Collection Item

## Structure

`CreateCatalogCollectionItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Asset` | [`models.Asset1`](../../doc/models/asset-1.md) | Required | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    createCatalogCollectionItem := models.CreateCatalogCollectionItem{
        Asset:                models.Asset1{
            Id:                   models.ToPointer("1690105108"),
            Type:                 "image",
        },
    }

}
```

