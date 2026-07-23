# Users

```go
usersController := client.UsersController()
```

## Class Name

`UsersController`

## Methods

* [Get User](../../doc/controllers/users.md#get-user)
* [Get Access Token](../../doc/controllers/users.md#get-access-token)
* [Get User Subscription List](../../doc/controllers/users.md#get-user-subscription-list)


# Get User

```go
GetUser(
    ctx context.Context) (
    models.ApiResponse[models.UserDetails],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Requires scope

### customer_accessCode

`user.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.UserDetails](../../doc/models/user-details.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := usersController.GetUser(ctx)
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


# Get Access Token

```go
GetAccessToken(
    ctx context.Context) (
    models.ApiResponse[models.AccessTokenDetails],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.AccessTokenDetails](../../doc/models/access-token-details.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := usersController.GetAccessToken(ctx)
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


# Get User Subscription List

```go
GetUserSubscriptionList(
    ctx context.Context) (
    models.ApiResponse[models.SubscriptionDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Requires scope

### customer_accessCode

`purchases.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.SubscriptionDataList](../../doc/models/subscription-data-list.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := usersController.GetUserSubscriptionList(ctx)
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

