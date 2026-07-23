
# O Auth Token

OAuth 2 Authorization endpoint response

## Structure

`OAuthToken`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccessToken` | `string` | Required | Access token |
| `TokenType` | `string` | Required | Type of access token |
| `ExpiresIn` | `*int64` | Optional | Time in seconds before the access token expires |
| `Scope` | `*string` | Optional | List of scopes granted<br>This is a space-delimited list of strings. |
| `Expiry` | `*int64` | Optional | Time of token expiry as unix timestamp (UTC) |
| `RefreshToken` | `*string` | Optional | Refresh token<br>Used to get a new access token when it expires. |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    oAuthToken := models.OAuthToken{
        AccessToken:  "access_token2",
        TokenType:    "token_type2",
        ExpiresIn:    models.ToPointer(int64(84)),
        Scope:        models.ToPointer("scope8"),
        Expiry:       models.ToPointer(int64(78)),
        RefreshToken: models.ToPointer("refresh_token4"),
    }

}
```

