
# Genre List

List of audio genres

## Structure

`GenreList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | `[]string` | Required | List of genres |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    genreList := models.GenreList{
        Data: []string{
            "Rock",
            "Pop > Singer-Songwriter",
            "Pop > Synth Pop",
            "Production / Film Scores",
        },
    }

}
```

