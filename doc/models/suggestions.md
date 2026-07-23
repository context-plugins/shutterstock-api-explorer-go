
# Suggestions

List of search suggestions

## Structure

`Suggestions`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | `[]string` | Optional | Search suggestions |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    suggestions := models.Suggestions{
        Data:                 []string{
            "cat scan",
            "cats and dogs",
            "cats playing",
            "catsuit",
            "cat silhouette",
            "catskills",
            "cats eyes",
            "cat sitting",
            "cat sleeping",
            "cats eye",
        },
    }

}
```

