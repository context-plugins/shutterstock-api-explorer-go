
# Editorial Category Results

List of editorial categories

## Structure

`EditorialCategoryResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.EditorialCategory`](../../doc/models/editorial-category.md) | Optional | List of editorial categories |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    editorialCategoryResults := models.EditorialCategoryResults{
        Data:                 []models.EditorialCategory{
            models.EditorialCategory{
                Name:                 models.ToPointer("Animal"),
            },
            models.EditorialCategory{
                Name:                 models.ToPointer("Awards"),
            },
            models.EditorialCategory{
                Name:                 models.ToPointer("Art"),
            },
        },
    }

}
```

