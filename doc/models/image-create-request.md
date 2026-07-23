
# Image Create Request

Request to upload an image

## Structure

`ImageCreateRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Base64Image` | `string` | Required | A Base 64 encoded jpeg or png; images can be no larger than 10mb and can be no larger than 10,000 pixels in width or height |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    imageCreateRequest := models.ImageCreateRequest{
        Base64Image:          "R0lGODlhgACAAPcAAEwiBLyaLOzNUNmWFNjOrNSuN7x6PPzqeOTMgfKSDMyuTPzwsdi2dHwuBPzbVu",
    }

}
```

