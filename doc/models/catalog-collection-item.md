
# Catalog Collection Item

Metadata about an item that is part of a collection

## Structure

`CatalogCollectionItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Asset` | [`models.Asset`](../../doc/models/asset.md) | Required | - |
| `CollectionIds` | `[]string` | Optional | The collection IDs that this asset belongs to |
| `CreatedTime` | `time.Time` | Required | - |
| `Id` | `string` | Required | - |

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
    catalogCollectionItem := models.CatalogCollectionItem{
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
    }

}
```

