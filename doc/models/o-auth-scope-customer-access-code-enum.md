
# O Auth Scope Customer Access Code Enum

OAuth 2 scopes supported by the API

## Enumeration

`OAuthScopeCustomerAccessCodeEnum`

## Fields

| Name | Description |
|  --- | --- |
| `COLLECTIONSEDIT` | Grant the ability to create new collections, edit a collection, and modify the contents of a collection |
| `COLLECTIONSVIEW` | Grant read-only access to a collection and its contents. |
| `LICENSESCREATE` | Grant the ability to download and license media on behalf of the user. |
| `LICENSESVIEW` | Grant read-only access to a user's licenses. |
| `PURCHASESVIEW` | Grant read-only access to a user's purchase history. |
| `USERVIEW` | *Originally missing* |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    oAuthScopeCustomerAccessCode := models.OAuthScopeCustomerAccessCodeEnum_COLLECTIONSEDIT

}
```

