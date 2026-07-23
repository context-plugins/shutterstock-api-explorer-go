
# Remove Catalog Collection Items

## Structure

`RemoveCatalogCollectionItems`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Items` | [`[]models.RemoveCatalogCollectionItem`](../../doc/models/remove-catalog-collection-item.md) | Required | **Constraints**: *Minimum Items*: `1`, *Maximum Items*: `50` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    removeCatalogCollectionItems := models.RemoveCatalogCollectionItems{
        Items:                []models.RemoveCatalogCollectionItem{
            models.RemoveCatalogCollectionItem{
                Id:                   "123",
            },
        },
    }

}
```

