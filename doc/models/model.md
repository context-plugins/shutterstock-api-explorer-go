
# Model

Information about a human model or property that appears in media; used to search for assets that this model is in

## Structure

`Model`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `string` | Required | ID of the model |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    model := models.Model{
        Id:                   "123456789",
    }

}
```

