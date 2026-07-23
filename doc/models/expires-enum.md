
# Expires Enum

Whether or not the token expires, expiring tokens come with a refresh_token to renew the access_token

## Enumeration

`ExpiresEnum`

## Fields

| Name |
|  --- |
| `TRUE` |
| `FALSE` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    expires := models.ExpiresEnum_TRUE

}
```

