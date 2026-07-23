
# Grant Type Enum

Grant type: authorization_code generates user tokens, client_credentials generates short-lived client grants

## Enumeration

`GrantTypeEnum`

## Fields

| Name |
|  --- |
| `AUTHORIZATIONCODE` |
| `CLIENTCREDENTIALS` |
| `REFRESHTOKEN` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    grantType := models.GrantTypeEnum_CLIENTCREDENTIALS

}
```

