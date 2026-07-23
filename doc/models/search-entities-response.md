
# Search Entities Response

The response to a request for keyword analysis

## Structure

`SearchEntitiesResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Keywords` | `[]string` | Optional | The top keywords from the submitted text |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    searchEntitiesResponse := models.SearchEntitiesResponse{
        Keywords:             []string{
            "planting",
            "flowers",
            "springtime",
            "beautiful",
        },
    }

}
```

