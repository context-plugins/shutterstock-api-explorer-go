
# Oauth Access Token Response

Access token response to client apps

## Structure

`OauthAccessTokenResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccessToken` | `string` | Required | Access token that can be used for future requests |
| `ExpiresIn` | `*int` | Optional | Number of seconds before token expires, only present for expiring tokens |
| `RefreshToken` | `*string` | Optional | A refresh token that can be used to renew the access_token when it expires, only present for expiring tokens |
| `TokenType` | `string` | Required | Type of token<br><br>**Default**: `"Bearer"` |
| `UserToken` | `*string` | Optional | Metadata about the access_token, only present for expiring tokens |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    oauthAccessTokenResponse := models.OauthAccessTokenResponse{
        AccessToken:          "v2/NmQwOTc0NTBiMjA5YzZkY2Q4NTkvMTA4OTg1MDk5L2N1c3RvbWVyLzIvZjB2a0RseGo4Rkt6ZjRmVWJNMm10V2VzcHh1NTBlZWJ6andUQU1NeTVYYnNFTDVWOFRJakItS2RnZTlmbEY1Y3haNWdXLUtYc2JhaXo5djk0V0p2QzZUUWZ4c2FNWm41NkdLYUgyVWlCaVUtQTNVMV9YQWpzd3lpblI3SlZEem8wSG1qQ2NzSkJlX3VQTnNXenBIdkd4SXViVi1rRGJTVENCV0g1U3U0RXRJSV9rSm5lQkl5QXlvbm5JN241UUhv",
        ExpiresIn:            models.ToPointer(182),
        RefreshToken:         models.ToPointer("refresh_token6"),
        TokenType:            "Bearer",
        UserToken:            models.ToPointer("user_token8"),
    }

}
```

