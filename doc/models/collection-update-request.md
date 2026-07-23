
# Collection Update Request

Collection update request

## Structure

`CollectionUpdateRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Name` | `string` | Required | The new name of the collection |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    collectionUpdateRequest := models.CollectionUpdateRequest{
        Name:                 "My collection with a new name",
    }

}
```

