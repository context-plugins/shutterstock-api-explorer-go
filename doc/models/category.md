
# Category

Category information

## Structure

`Category`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*string` | Optional | Category ID |
| `Name` | `*string` | Optional | Category name |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    category := models.Category{
        Id:                   models.ToPointer("1"),
        Name:                 models.ToPointer("Animals/Wildlife"),
    }

}
```

