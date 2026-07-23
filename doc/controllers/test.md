# Test

```go
testController := client.TestController()
```

## Class Name

`TestController`

## Methods

* [Echo](../../doc/controllers/test.md#echo)
* [Validate](../../doc/controllers/test.md#validate)


# Echo

:information_source: **Note** This endpoint does not require authentication.

```go
Echo(
    ctx context.Context,
    text *string) (
    models.ApiResponse[models.TestEcho],
    error)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `text` | `*string` | Query, Optional | Text to echo<br><br>**Default**: `"ok"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.TestEcho](../../doc/models/test-echo.md).

## Example Usage

```go
ctx := context.Background()

text := "ok"

apiResponse, err := testController.Echo(ctx, &text)
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


# Validate

:information_source: **Note** This endpoint does not require authentication.

```go
Validate(
    ctx context.Context,
    id int,
    tag []string,
    userAgent *string) (
    models.ApiResponse[models.TestValidate],
    error)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `int` | Query, Required | Integer ID |
| `tag` | `[]string` | Query, Optional | List of tags |
| `userAgent` | `*string` | Header, Optional | User agent |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.TestValidate](../../doc/models/test-validate.md).

## Example Usage

```go
ctx := context.Background()

id := 123

apiResponse, err := testController.Validate(ctx, id, nil, nil)
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

