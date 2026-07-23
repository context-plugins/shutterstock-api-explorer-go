
# Catalog Collection Role Assignments

List of role assignments for a catalog collection

## Structure

`CatalogCollectionRoleAssignments`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CollectionId` | `string` | Required | - |
| `Roles` | [`models.Roles`](../../doc/models/roles.md) | Required | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    catalogCollectionRoleAssignments := models.CatalogCollectionRoleAssignments{
        CollectionId:         "126351028",
        Roles:                models.Roles{
            Editors:              []models.CatalogCollectionRole{
                models.CatalogCollectionRole{
                    Email:                "userTwo@org.com",
                    Id:                   "987",
                    Type:                 "USER",
                },
            },
            Owners:               []models.CatalogCollectionRole{
                models.CatalogCollectionRole{
                    Email:                "userOne@org.com",
                    Id:                   "321",
                    Type:                 "USER",
                },
            },
            Viewers:              []models.CatalogCollectionRole{
            },
        },
    }

}
```

