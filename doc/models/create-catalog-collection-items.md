
# Create Catalog Collection Items

## Structure

`CreateCatalogCollectionItems`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Items` | [`[]models.CreateCatalogCollectionItem`](../../doc/models/create-catalog-collection-item.md) | Required | **Constraints**: *Minimum Items*: `1`, *Maximum Items*: `50` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    createCatalogCollectionItems := models.CreateCatalogCollectionItems{
        Items:                []models.CreateCatalogCollectionItem{
            models.CreateCatalogCollectionItem{
                Asset:                models.Asset1{
                    Id:                   models.ToPointer("1690105108"),
                    Type:                 "image",
                },
            },
        },
    }

}
```

