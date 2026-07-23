# Computer Vision

```go
computerVisionController := client.ComputerVisionController()
```

## Class Name

`ComputerVisionController`

## Methods

* [Upload Image](../../doc/controllers/computer-vision.md#upload-image)
* [Get Keywords](../../doc/controllers/computer-vision.md#get-keywords)
* [Get Similar Images](../../doc/controllers/computer-vision.md#get-similar-images)
* [Get Similar Videos](../../doc/controllers/computer-vision.md#get-similar-videos)
* [Upload Ephemeral Image](../../doc/controllers/computer-vision.md#upload-ephemeral-image)


# Upload Image

This endpoint uploads an image for reverse image or video search. Images must be in JPEG or PNG format. To get the search results, pass the upload ID that this endpoint returns to the GET /v2/cv/similar/images or GET /v2/cv/similar/videos endpoints. Contact us for access to this endpoint.

```go
UploadImage(
    ctx context.Context,
    body models.ImageCreateRequest) (
    models.ApiResponse[models.ComputerVisionImageCreateResponse],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.ImageCreateRequest`](../../doc/models/image-create-request.md) | Body, Required | A Base 64 encoded jpeg or png; images can be no larger than 10mb and can be no larger than 10,000 pixels in width or height |

## Response Type

**201**: Created

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.ComputerVisionImageCreateResponse](../../doc/models/computer-vision-image-create-response.md).

## Example Usage

```go
ctx := context.Background()

body := models.ImageCreateRequest{
    Base64Image:          "R0lGODlhgACAAPcAAEwiBLyaLOzNUNmWFNjOrNSuN7x6PPzqeOTMgfKSDMyuTPzwsdi2dHwuBPzbVu",
}

apiResponse, err := computerVisionController.UploadImage(ctx, body)
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
| 413 | Payload Too Large | `ApiError` |
| 415 | Unsupported Media Type | `ApiError` |


# Get Keywords

This endpoint returns a list of suggested keywords for a media item that you specify or upload.

```go
GetKeywords(
    ctx context.Context,
    assetId models.GetKeywordsAssetId) (
    models.ApiResponse[models.KeywordDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `assetId` | [`models.GetKeywordsAssetId`](../../doc/models/containers/get-keywords-asset-id.md) | Query, Required | This is a container for one-of cases. |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.KeywordDataList](../../doc/models/keyword-data-list.md).

## Example Usage

```go
ctx := context.Background()

assetId := models.GetKeywordsAssetIdContainer.FromString("U6ba16262e3bc2db470b8e3cfa8aaab25")

apiResponse, err := computerVisionController.GetKeywords(ctx, assetId)
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
| 415 | Unsupported Media Type | `ApiError` |


# Get Similar Images

This endpoint returns images that are visually similar to an image that you specify or upload.

```go
GetSimilarImages(
    ctx context.Context,
    assetId string,
    license []models.License5Enum,
    safe *bool,
    language *models.LanguageEnum,
    page *int,
    perPage *int,
    view *models.View1Enum) (
    models.ApiResponse[models.ImageSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `assetId` | `string` | Query, Required | The asset ID or upload ID to find similar images for |
| `license` | [`[]models.License5Enum`](../../doc/models/license-5-enum.md) | Query, Optional | Show only images with the specified license |
| `safe` | `*bool` | Query, Optional | Enable or disable safe search<br><br>**Default**: `true` |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Language for the keywords and categories in the response |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 500` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.ImageSearchResults](../../doc/models/image-search-results.md).

## Example Usage

```go
ctx := context.Background()

assetId := "U6ba16262e3bc2db470b8e3cfa8aaab25"

safe := true

language := models.LanguageEnum_ES

page := 1

perPage := 20

view := models.View1Enum_MINIMAL

apiResponse, err := computerVisionController.GetSimilarImages(ctx, assetId, nil, &safe, &language, &page, &perPage, &view)
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


# Get Similar Videos

This endpoint returns videos that are visually similar to an image that you specify or upload.

```go
GetSimilarVideos(
    ctx context.Context,
    assetId string,
    license []models.License5Enum,
    safe *bool,
    language *models.LanguageEnum,
    page *int,
    perPage *int,
    view *models.View1Enum) (
    models.ApiResponse[models.VideoSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `assetId` | `string` | Query, Required | The asset ID or upload ID to find similar videos for |
| `license` | [`[]models.License5Enum`](../../doc/models/license-5-enum.md) | Query, Optional | Show only videos with the specified license |
| `safe` | `*bool` | Query, Optional | Enable or disable safe search<br><br>**Default**: `true` |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Language for the keywords and categories in the response |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 500` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.VideoSearchResults](../../doc/models/video-search-results.md).

## Example Usage

```go
ctx := context.Background()

assetId := "U6ba16262e3bc2db470b8e3cfa8aaab25"

safe := true

language := models.LanguageEnum_ES

page := 1

perPage := 20

view := models.View1Enum_MINIMAL

apiResponse, err := computerVisionController.GetSimilarVideos(ctx, assetId, nil, &safe, &language, &page, &perPage, &view)
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


# Upload Ephemeral Image

**This endpoint is deprecated.**

Deprecated; use `POST /v2/cv/images` instead. This endpoint uploads an image for reverse image search. The image must be in JPEG or PNG format. To get the search results, pass the ID that this endpoint returns to the `GET /v2/images/{id}/similar` endpoint.

```go
UploadEphemeralImage(
    ctx context.Context,
    body models.ImageCreateRequest) (
    models.ApiResponse[models.ImageCreateResponse],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.ImageCreateRequest`](../../doc/models/image-create-request.md) | Body, Required | The image data in JPEG or PNG format |

## Response Type

**201**: Created

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.ImageCreateResponse](../../doc/models/image-create-response.md).

## Example Usage

```go
ctx := context.Background()

body := models.ImageCreateRequest{
    Base64Image:          "R0lGODlhgACAAPcAAEwiBLyaLOzNUNmWFNjOrNSuN7x6PPzqeOTMgfKSDMyuTPzwsdi2dHwuBPzbVu",
}

apiResponse, err := computerVisionController.UploadEphemeralImage(ctx, body)
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
| 413 | Payload Too Large | `ApiError` |

