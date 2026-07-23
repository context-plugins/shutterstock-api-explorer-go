
# Sfx Url

Sound effect license URL object

## Structure

`SfxUrl`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Url` | `string` | Required | URL that can be used to download the unwatermarked, licensed asset |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    sfxUrl := models.SfxUrl{
        Url:                  "url2",
    }

}
```

