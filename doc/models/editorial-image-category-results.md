
# Editorial Image Category Results

List of editorial categories

## Structure

`EditorialImageCategoryResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.EditorialCategory`](../../doc/models/editorial-category.md) | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    editorialImageCategoryResults := models.EditorialImageCategoryResults{
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
            models.EditorialCategory{
                Name:                 models.ToPointer("Film Stills"),
            },
        },
    }

}
```

