
# Editorial Category

Name of an editorial category

## Structure

`EditorialCategory`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Name` | `*string` | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    editorialCategory := models.EditorialCategory{
        Name:                 models.ToPointer("Awards"),
    }

}
```

