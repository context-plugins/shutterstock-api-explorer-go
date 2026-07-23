
# Album

Album metadata

## Structure

`Album`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `string` | Required | The album ID |
| `Title` | `string` | Required | The album title |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    album := models.Album{
        Id:    "1234567",
        Title: "Happy Music",
    }

}
```

