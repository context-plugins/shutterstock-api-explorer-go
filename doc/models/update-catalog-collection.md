
# Update Catalog Collection

## Structure

`UpdateCatalogCollection`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CoverAsset` | [`*models.RemoveCatalogCollectionItem`](../../doc/models/remove-catalog-collection-item.md) | Optional | - |
| `Name` | `*string` | Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100000` |
| `Visibility` | [`*models.VisibilityEnum`](../../doc/models/visibility-enum.md) | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    updateCatalogCollection := models.UpdateCatalogCollection{
        CoverAsset:           models.ToPointer(models.RemoveCatalogCollectionItem{
            Id:                   "123",
        }),
        Name:                 models.ToPointer("My Collection"),
        Visibility:           models.ToPointer(models.VisibilityEnum_PUBLIC),
    }

}
```

