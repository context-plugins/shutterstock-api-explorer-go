
# Featured Collection Cover Item

Featured collection cover item metadata

## Structure

`FeaturedCollectionCoverItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Url` | `string` | Required | URL of the collection cover item |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    featuredCollectionCoverItem := models.FeaturedCollectionCoverItem{
        Url:                  "https://ak.picdn.net/assets/cms/b467415246debdab45825d915a548f8f79b57882-Collection_1_Thumnail.jpg",
    }

}
```

