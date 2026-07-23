
# Model Release

Model and property release metadata

## Structure

`ModelRelease`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `*string` | Optional | ID of the model or property release |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    modelRelease := models.ModelRelease{
        Id:                   models.ToPointer("123456789"),
    }

}
```

