
# Catalog Collection Item Data List

List of catalog collection items

## Structure

`CatalogCollectionItemDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.CatalogCollectionItem`](../../doc/models/catalog-collection-item.md) | Required | List of catalog collection items |
| `Page` | `float64` | Required | - |
| `PerPage` | `float64` | Required | - |
| `TotalCount` | `float64` | Required | - |

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
    catalogCollectionItemDataList := models.CatalogCollectionItemDataList{
        Data:                 []models.CatalogCollectionItem{
            models.CatalogCollectionItem{
                Asset:                models.Asset{
                    Id:                   models.ToPointer("1690105108"),
                    Name:                 models.ToPointer("Young couple playing tennis at the court"),
                    Type:                 models.Type1Enum_IMAGE,
                },
                CollectionIds:        []string{
                    "126351028",
                },
                CreatedTime:          parseTime(time.RFC3339, "2021-06-10T13:26:09-04:00", func(err error) { log.Fatalln(err) }),
                Id:                   "123",
            },
        },
        Page:                 float64(1),
        PerPage:              float64(1),
        TotalCount:           float64(82),
    }

}
```

