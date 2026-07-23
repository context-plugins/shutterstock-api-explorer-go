
# Cookie

Cookie object

## Structure

`Cookie`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Name` | `string` | Required | The name of the cookie |
| `Value` | `string` | Required | The value of the cookie |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    cookie := models.Cookie{
        Name:                 "The name of the cookie",
        Value:                "The value of the cookie",
    }

}
```

