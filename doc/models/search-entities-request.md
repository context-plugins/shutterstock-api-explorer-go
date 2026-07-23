
# Search Entities Request

Search entity request data

## Structure

`SearchEntitiesRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Text` | `string` | Required | Plain text to extract keywords from<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100000` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    searchEntitiesRequest := models.SearchEntitiesRequest{
        Text:                 "Planting flowers is a great way to make springtime more beautiful.",
    }

}
```

