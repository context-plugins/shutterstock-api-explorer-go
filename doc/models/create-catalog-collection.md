
# Create Catalog Collection

## Structure

`CreateCatalogCollection`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Items` | [`[]models.CreateCatalogCollectionItem`](../../doc/models/create-catalog-collection-item.md) | Optional | **Constraints**: *Maximum Items*: `50` |
| `Name` | `string` | Required | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100000` |
| `Visibility` | [`*models.VisibilityEnum`](../../doc/models/visibility-enum.md) | Optional | **Default**: `"private"` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    createCatalogCollection := models.CreateCatalogCollection{
        Items:                []models.CreateCatalogCollectionItem{
            models.CreateCatalogCollectionItem{
                Asset:                models.Asset1{
                    Id:                   models.ToPointer("1690105108"),
                    Type:                 "image",
                },
            },
        },
        Name:                 "New Collection",
        Visibility:           models.ToPointer(models.VisibilityEnum_PUBLIC),
    }

}
```

