
# Artist

Metadata about the artist that created the media

## Structure

`Artist`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Name` | `string` | Required | The artist's name |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    artist := models.Artist{
        Name:                 "The Happy Tunes Band",
    }

}
```

