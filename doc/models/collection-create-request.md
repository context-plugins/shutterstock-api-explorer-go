
# Collection Create Request

Collection creation request

## Structure

`CollectionCreateRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Name` | `string` | Required | The name of the collection |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    collectionCreateRequest := models.CollectionCreateRequest{
        Name:                 "Test Collection 19cf",
    }

}
```

