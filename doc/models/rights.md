
# Rights

## Structure

`Rights`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Countries` | `*string` | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    rights := models.Rights{
        Countries:            models.ToPointer("countries0"),
    }

}
```

