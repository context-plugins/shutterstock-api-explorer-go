
# Url

URL object

## Structure

`Url`

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
    url := models.Url{
        Url:                  "https://download.shutterstock.com/gatekeeper/[random-characters]/shutterstock_59656357.jpg",
    }

}
```

