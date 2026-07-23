
# OAuth 2 Authorization Code Grant



Documentation for accessing and setting credentials for customer_accessCode.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| oAuthClientId | `string` | OAuth 2 Client ID | `WithOAuthClientId` | `OAuthClientId()` |
| oAuthClientSecret | `string` | OAuth 2 Client Secret | `WithOAuthClientSecret` | `OAuthClientSecret()` |
| oAuthRedirectUri | `string` | OAuth 2 Redirection endpoint or Callback Uri | `WithOAuthRedirectUri` | `OAuthRedirectUri()` |
| oAuthToken | `OAuthToken` | Object for storing information about the OAuth token | `WithOAuthToken` | `OAuthToken()` |
| oAuthScopes | `[]OAuthScopeCustomerAccessCodeEnum` | List of scopes that apply to the OAuth token | `WithOAuthScopes` | `OAuthScopes()` |



**Note:** Required auth credentials can be set using `WithCustomerAccessCodeCredentials()` by providing a credentials instance with `NewCustomerAccessCodeCredentials()` in the configuration initialization and accessed using the `CustomerAccessCodeCredentials()` method in the configuration instance.

## Usage Example

### 1\. Client Initialization

You must initialize the client with *OAuth 2.0 Authorization Code Grant* credentials as shown in the following code snippet.

```go
package main

import (
    "shutterstockapiexplorer"
    "shutterstockapiexplorer/models"
)

func main() {
    client := shutterstockapiexplorer.NewClient(
    shutterstockapiexplorer.CreateConfiguration(
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



Your application must obtain user authorization before it can execute an endpoint call in case this SDK chooses to use *OAuth 2.0 Authorization Code Grant*. This authorization includes the following steps

### 2\. Obtain user consent

To obtain user's consent, you must redirect the user to the authorization page.The `BuildAuthorizationURL` method creates the URL to the authorization page. You must have initialized the client with scopes for which you need permission to access.

```go
state := "session-state"
url := client.CustomerAccessCodeManager().BuildAuthorizationURL(state)
// redirect the user to the given URL and get a code after the user consents
```

### 3\. Handle the OAuth server response

Once the user responds to the consent request, the OAuth 2.0 server responds to your application's access request by redirecting the user to the redirect URI specified set in `Configuration`.

If the user approves the request, the authorization code will be sent as the `code` query string:

```
https://example.com/oauth/callback?code=XXXXXXXXXXXXXXXXXXXXXXXXX
```

If the user does not approve the request, the response contains an `error` query string:

```
https://example.com/oauth/callback?error=access_denied
```

### 4\. Authorize the client using the code

After the server receives the code, it can exchange this for an *access token*. The access token is an object containing information for authorizing client requests and refreshing the token itself.

```go
oAuthToken, err := client.CustomerAccessCodeManager().FetchToken(ctx, authCode)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the token
    fmt.Println(oAuthToken)
}

// Creating a new client with the token
client = client.CloneWithConfiguration(
    shutterstockapiexplorer.WithCustomerAccessCodeCredentials(
        client.Configuration().CustomerAccessCodeCredentials().
            WithOAuthToken(oAuthToken),
    ),
)
```

### Scopes

Scopes enable your application to only request access to the resources it needs while enabling users to control the amount of access they grant to your application. Available scopes are defined in the [`OAuthScopeCustomerAccessCodeEnum`](../../doc/models/o-auth-scope-customer-access-code-enum.md) enumeration.

| Scope Name | Description |
|  --- | --- |
| `COLLECTIONS_EDIT` | Grant the ability to create new collections, edit a collection, and modify the contents of a collection |
| `COLLECTIONS_VIEW` | Grant read-only access to a collection and its contents. |
| `LICENSES_CREATE` | Grant the ability to download and license media on behalf of the user. |
| `LICENSES_VIEW` | Grant read-only access to a user's licenses. |
| `PURCHASES_VIEW` | Grant read-only access to a user's purchase history. |
| `USER_VIEW` | *Originally missing* |

### Refreshing the token

An access token may expire after sometime. To extend its lifetime, you must refresh the token.

```go
if client.CustomerAccessCodeManager().OAuthTokenIsExpired() {
    oAuthToken, err := client.CustomerAccessCodeManager().RefreshToken(ctx)
    if err != nil {
        log.Fatalln(err)
    } else {
        // Printing the token
        fmt.Println(oAuthToken)
    }

    // Creating a new client with the token
    client = client.CloneWithConfiguration(
        shutterstockapiexplorer.WithCustomerAccessCodeCredentials(
            client.Configuration().CustomerAccessCodeCredentials().
                WithOAuthToken(oAuthToken),
        ),
    )
}
```

If a token expires, an error will be returned before the next endpoint call requiring authentication.

### Storing an access token for reuse

It is recommended that you store the access token for reuse.

```go
oAuthToken := client.Configuration().CustomerAccessCodeCredentials().OAuthToken()
StoreInDatabase(oAuthToken)
```

### Creating a client from a stored token

To authorize a client using a stored access token, just set the access token in Configuration along with the other configuration parameters before creating the client:

```go
// Get token from storage
oAuthToken := GetStoredToken()

// Creating a new client with the token
client = client.CloneWithConfiguration(
    shutterstockapiexplorer.WithCustomerAccessCodeCredentials(
        client.Configuration().CustomerAccessCodeCredentials().
            WithOAuthToken(oAuthToken),
    ),
)
```

### Complete example



```go
package main

import (
    "context"
    "fmt"
    "log"
    "shutterstockapiexplorer"
    "shutterstockapiexplorer/models"
)

func main() {
    ctx := context.Background()
    
    // Client configuration
    package main
    import (
        "shutterstockapiexplorer"
        "shutterstockapiexplorer/models"
    )
    func main() {
        client := shutterstockapiexplorer.NewClient(
        shutterstockapiexplorer.CreateConfiguration(
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
    
    // Obtain access token, restore from cache if possible
    if oAuthToken, err := GetStoredToken(); err == nil {
        // Refresh the token if it is expired
        if client.CustomerAccessCodeManager().OAuthTokenIsExpired() {
            oAuthToken, err = client.CustomerAccessCodeManager().RefreshToken(ctx)
            if err != nil {
                log.Fatalln(err)
            } else {
                // Printing the token
                fmt.Println(oAuthToken)
            }
        }
        
        // Creating a new client with the token
        client = client.CloneWithConfiguration(
            shutterstockapiexplorer.WithCustomerAccessCodeCredentials(
                client.Configuration().CustomerAccessCodeCredentials().
                    WithOAuthToken(oAuthToken),
            ),
        )
    } else {
        // build authorization url to redirect the user
        state := "session-state"
        url := client.CustomerAccessCodeManager().BuildAuthorizationURL(state)
        // redirect the user to the given URL and get a code after the user consents
        authCode := GetAuthCode(url)
        
        // Fetch an access token to authorize the client
        oAuthToken, err := client.CustomerAccessCodeManager().FetchToken(ctx, authCode)
        if err != nil {
            log.Fatalln(err)
        } else {
            // Printing the token
            fmt.Println(oAuthToken)
        }
        
        // Creating a new client with the token
        client = client.CloneWithConfiguration(
            shutterstockapiexplorer.WithCustomerAccessCodeCredentials(
                client.Configuration().CustomerAccessCodeCredentials().
                    WithOAuthToken(oAuthToken),
            ),
        )
        
        // Store the token
        StoreInDatabase(oAuthToken)
    }
    
    // The client is now authorized; you can use the client to make endpoint calls
}

func GetStoredToken() (
    models.OAuthToken,
    error) {
    // Get token logic here
    return models.OAuthToken{}, nil
}

func StoreInDatabase(oAuthToken models.OAuthToken) {
    // Save token logic here
}

func GetAuthCode(redirectURL string) string {
    // User redirection logic here
    return ""
}
```


