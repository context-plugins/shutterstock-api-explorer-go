
# Catalog Collection

Catalog collection

## Structure

`CatalogCollection`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CoverAsset` | [`*models.CatalogCollectionItem`](../../doc/models/catalog-collection-item.md) | Optional | Metadata about an item that is part of a collection |
| `CreatedTime` | `time.Time` | Required | - |
| `Id` | `string` | Required | - |
| `Name` | `string` | Required | - |
| `RoleAssignments` | [`models.CatalogCollectionRoleAssignments`](../../doc/models/catalog-collection-role-assignments.md) | Required | List of role assignments for a catalog collection |
| `TotalItemCount` | `float64` | Required | - |
| `UpdatedTime` | `time.Time` | Required | - |
| `Visibility` | [`models.VisibilityEnum`](../../doc/models/visibility-enum.md) | Required | - |

## Example

```go
package main

import (
    "log"
    "time"
    "shutterstockapiexplorer/models"
)

func main() {
    parseTime := func(layout, value string, errCallback func(error)) time.Time {
        dateTime, err := time.Parse(layout, value)
        if err != nil {
            errCallback(err) 
       }
        return dateTime
    }
    catalogCollection := models.CatalogCollection{
        CoverAsset:           models.ToPointer(models.CatalogCollectionItem{
            Asset:                models.Asset{
                Id:                   models.ToPointer("1690105108"),
                Name:                 models.ToPointer("Young couple playing tennis at the court"),
                Type:                 models.Type1Enum_IMAGE,
            },
            CollectionIds:        []string{
                "collection_ids5",
                "collection_ids6",
            },
            CreatedTime:          parseTime(time.RFC3339, "2021-06-10T13:26:09-04:00", func(err error) { log.Fatalln(err) }),
            Id:                   "123",
        }),
        CreatedTime:          parseTime(time.RFC3339, "2021-05-20T16:15:22-04:00", func(err error) { log.Fatalln(err) }),
        Id:                   "126351028",
        Name:                 "My collection",
        RoleAssignments:      models.CatalogCollectionRoleAssignments{
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
        },
        TotalItemCount:       float64(2),
        UpdatedTime:          parseTime(time.RFC3339, "2021-06-10T13:26:09-04:00", func(err error) { log.Fatalln(err) }),
        Visibility:           models.VisibilityEnum_PUBLIC,
    }

}
```

