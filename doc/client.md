
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| httpConfiguration | [`HttpConfiguration`](../doc/http-configuration.md) | Configurable http client options like timeout and retries. |
| basicCredentials | [`BasicCredentials`](auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |
| customerAccessCodeCredentials | [`CustomerAccessCodeCredentials`](auth/oauth-2-authorization-code-grant.md) | The Credentials Setter for OAuth 2 Authorization Code Grant |

The API client can be initialized as follows:

```go
package main

import (
    "shutterstockapiexplorer"
    "shutterstockapiexplorer/models"
)

func main() {
    client := shutterstockapiexplorer.NewClient(
    shutterstockapiexplorer.CreateConfiguration(
            shutterstockapiexplorer.WithHttpConfiguration(
                shutterstockapiexplorer.CreateHttpConfiguration(
                    shutterstockapiexplorer.WithTimeout(0),
                ),
            ),
            shutterstockapiexplorer.WithEnvironment(shutterstockapiexplorer.PRODUCTION),
            shutterstockapiexplorer.WithBasicCredentials(
                shutterstockapiexplorer.NewBasicCredentials(
                    "Username",
                    "Password",
                ),
            ),
            shutterstockapiexplorer.WithCustomerAccessCodeCredentials(
                shutterstockapiexplorer.NewCustomerAccessCodeCredentials(
                    "OAuthClientId",
                    "OAuthClientSecret",
                    "OAuthRedirectUri",
                ).
                WithOAuthScopes([]models.OAuthScopeCustomerAccessCodeEnum{
        models.OAuthScopeCustomerAccessCodeEnum_COLLECTIONSEDIT,
        models.OAuthScopeCustomerAccessCodeEnum_COLLECTIONSVIEW,
    }),
            ),
        ),
    )
}
```

## Shutterstock API Explorer Client

The gateway for the SDK. This class acts as a factory for the Controllers and also holds the configuration of the SDK.

## Controllers

| Name | Description |
|  --- | --- |
| CustomMusicController() | Gets CustomMusicController |
| AudioController() | Gets AudioController |
| ImagesController() | Gets ImagesController |
| CatalogController() | Gets CatalogController |
| ContributorsController() | Gets ContributorsController |
| ComputerVisionController() | Gets ComputerVisionController |
| EditorialImagesController() | Gets EditorialImagesController |
| EditorialVideoController() | Gets EditorialVideoController |
| OauthController() | Gets OauthController |
| SoundEffectsController() | Gets SoundEffectsController |
| TestController() | Gets TestController |
| UsersController() | Gets UsersController |
| VideosController() | Gets VideosController |
| OAuthAuthorizationController() | Gets OAuthAuthorizationController |

