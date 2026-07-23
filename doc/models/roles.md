
# Roles

## Structure

`Roles`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Editors` | [`[]models.CatalogCollectionRole`](../../doc/models/catalog-collection-role.md) | Optional | - |
| `Owners` | [`[]models.CatalogCollectionRole`](../../doc/models/catalog-collection-role.md) | Optional | - |
| `Viewers` | [`[]models.CatalogCollectionRole`](../../doc/models/catalog-collection-role.md) | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    roles := models.Roles{
        Editors:              []models.CatalogCollectionRole{
            models.CatalogCollectionRole{
                Email:                "email2",
                Id:                   "id4",
                Type:                 "type6",
            },
        },
        Owners:               []models.CatalogCollectionRole{
            models.CatalogCollectionRole{
                Email:                "email2",
                Id:                   "id4",
                Type:                 "type6",
            },
            models.CatalogCollectionRole{
                Email:                "email2",
                Id:                   "id4",
                Type:                 "type6",
            },
            models.CatalogCollectionRole{
                Email:                "email2",
                Id:                   "id4",
                Type:                 "type6",
            },
        },
        Viewers:              []models.CatalogCollectionRole{
            models.CatalogCollectionRole{
                Email:                "email8",
                Id:                   "id8",
                Type:                 "type2",
            },
        },
    }

}
```

