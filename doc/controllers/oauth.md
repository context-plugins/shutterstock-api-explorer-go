# Oauth

```go
oauthController := client.OauthController()
```

## Class Name

`OauthController`

## Methods

* [Create Access Token](../../doc/controllers/oauth.md#create-access-token)
* [Authorize](../../doc/controllers/oauth.md#authorize)


# Create Access Token

This endpoint returns an access token for the specified user and with the specified scopes. The token does not expire until the user changes their password. The body parameters must be encoded as form data.

:information_source: **Note** This endpoint does not require authentication.

```go
CreateAccessToken(
    ctx context.Context,
    clientId string,
    grantType models.GrantTypeEnum,
    clientSecret *string,
    code *string,
    expires *models.ExpiresEnum,
    realm *models.Realm1Enum,
    refreshToken *string) (
    models.ApiResponse[models.OauthAccessTokenResponse],
    error)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `clientId` | `string` | Form, Required | Client ID (Consumer Key) of your application |
| `grantType` | [`models.GrantTypeEnum`](../../doc/models/grant-type-enum.md) | Form, Required | Grant type: authorization_code generates user tokens, client_credentials generates short-lived client grants |
| `clientSecret` | `*string` | Form, Optional | Client Secret (Consumer Secret) of your application |
| `code` | `*string` | Form, Optional | Response code from the /oauth/authorize flow; required if grant_type=authorization_code |
| `expires` | [`*models.ExpiresEnum`](../../doc/models/expires-enum.md) | Form, Optional | Whether or not the token expires, expiring tokens come with a refresh_token to renew the access_token<br><br>**Default**: `"false"` |
| `realm` | [`*models.Realm1Enum`](../../doc/models/realm-1-enum.md) | Form, Optional | User type to be authorized (usually 'customer')<br><br>**Default**: `"customer"` |
| `refreshToken` | `*string` | Form, Optional | Pass this along with grant_type=refresh_token to get a fresh access token |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.OauthAccessTokenResponse](../../doc/models/oauth-access-token-response.md).

## Example Usage

```go
ctx := context.Background()

clientId := "141024g14g28104gff1h"

grantType := models.GrantTypeEnum_CLIENTCREDENTIALS

expires := models.ExpiresEnum_FALSE

realm := models.Realm1Enum_CUSTOMER

apiResponse, err := oauthController.CreateAccessToken(ctx, clientId, grantType, nil, nil, &expires, &realm, nil)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# Authorize

This endpoint returns a redirect URI (in the 'Location' header) that the customer uses to authorize your application and, together with POST /v2/oauth/access_token, generate an access token that represents that authorization.

:information_source: **Note** This endpoint does not require authentication.

```go
Authorize(
    ctx context.Context,
    clientId string,
    redirectUri string,
    responseType models.ResponseTypeEnum,
    state string,
    realm *models.Realm2Enum,
    scope *string) (
    http.Response,
    error)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `clientId` | `string` | Query, Required | Client ID (Consumer Key) of your application |
| `redirectUri` | `string` | Query, Required | The callback URI to send the request to after authorization; must use a host name that is registered with your application |
| `responseType` | [`models.ResponseTypeEnum`](../../doc/models/response-type-enum.md) | Query, Required | Type of temporary authorization code that will be used to generate an access code; the only valid value is 'code' |
| `state` | `string` | Query, Required | Unique value used by the calling app to verify the request |
| `realm` | [`*models.Realm2Enum`](../../doc/models/realm-2-enum.md) | Query, Optional | User type to be authorized (usually 'customer')<br><br>**Default**: `"customer"` |
| `scope` | `*string` | Query, Optional | Space-separated list of scopes to be authorized<br><br>**Default**: `"user.view"` |

## Response Type

**200**

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

clientId := "6d097450b209c6dcd859"

redirectUri := "localhost"

responseType := models.ResponseTypeEnum_CODE

state := "1540290465000"

realm := models.Realm2Enum_CUSTOMER

scope := "user.view"

resp, err := oauthController.Authorize(ctx, clientId, redirectUri, responseType, state, &realm, &scope)
if err != nil {
    log.Fatalln(err)
} else {
    fmt.Println(resp.StatusCode)
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |

