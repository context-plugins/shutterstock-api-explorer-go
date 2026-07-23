
# Editorial Cover Item

Cover image for editorial livefeed

## Structure

`EditorialCoverItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Height` | `*int` | Optional | - |
| `Id` | `string` | Required | - |
| `Url` | `string` | Required | - |
| `Width` | `*int` | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    editorialCoverItem := models.EditorialCoverItem{
        Height:               models.ToPointer(117),
        Id:                   "9763363q",
        Url:                  "https://editorial01.qa.shuttercorp.net/thumb/9763363q/51e28f39/Shutterstock_9763363q.jpg",
        Width:                models.ToPointer(170),
    }

}
```

