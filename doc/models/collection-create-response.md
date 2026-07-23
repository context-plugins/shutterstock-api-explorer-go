
# Collection Create Response

Collection creation response

## Structure

`CollectionCreateResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `string` | Required | ID of the new collection |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    collectionCreateResponse := models.CollectionCreateResponse{
        Id:                   "48433105",
    }

}
```

