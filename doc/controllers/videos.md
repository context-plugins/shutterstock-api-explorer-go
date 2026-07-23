# Videos

```go
videosController := client.VideosController()
```

## Class Name

`VideosController`

## Methods

* [Get Video List](../../doc/controllers/videos.md#get-video-list)
* [List Video Categories](../../doc/controllers/videos.md#list-video-categories)
* [Get Video Collection List](../../doc/controllers/videos.md#get-video-collection-list)
* [Create Video Collection](../../doc/controllers/videos.md#create-video-collection)
* [Get Featured Video Collection List](../../doc/controllers/videos.md#get-featured-video-collection-list)
* [Get Featured Video Collection](../../doc/controllers/videos.md#get-featured-video-collection)
* [Get Featured Video Collection Items](../../doc/controllers/videos.md#get-featured-video-collection-items)
* [Delete Video Collection](../../doc/controllers/videos.md#delete-video-collection)
* [Get Video Collection](../../doc/controllers/videos.md#get-video-collection)
* [Rename Video Collection](../../doc/controllers/videos.md#rename-video-collection)
* [Delete Video Collection Items](../../doc/controllers/videos.md#delete-video-collection-items)
* [Get Video Collection Items](../../doc/controllers/videos.md#get-video-collection-items)
* [Add Video Collection Items](../../doc/controllers/videos.md#add-video-collection-items)
* [Get Video License List](../../doc/controllers/videos.md#get-video-license-list)
* [License Videos](../../doc/controllers/videos.md#license-videos)
* [Download Videos](../../doc/controllers/videos.md#download-videos)
* [Search Videos](../../doc/controllers/videos.md#search-videos)
* [Get Video Suggestions](../../doc/controllers/videos.md#get-video-suggestions)
* [Get Updated Videos](../../doc/controllers/videos.md#get-updated-videos)
* [Get Video](../../doc/controllers/videos.md#get-video)
* [Find Similar Videos](../../doc/controllers/videos.md#find-similar-videos)


# Get Video List

This endpoint lists information about one or more videos, including the aspect ratio and URLs to previews.

```go
GetVideoList(
    ctx context.Context,
    id []string,
    view *models.View1Enum,
    searchId *string) (
    models.ApiResponse[models.VideoDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Required | One or more video IDs<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `500` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.VideoDataList](../../doc/models/video-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := []string{
    "639703",
    "993721",
}

view := models.View1Enum_MINIMAL

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := videosController.GetVideoList(ctx, id, &view, &searchId)
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


# List Video Categories

This endpoint lists the categories (Shutterstock-assigned genres) that videos can belong to.

```go
ListVideoCategories(
    ctx context.Context,
    language *models.LanguageEnum) (
    models.ApiResponse[models.CategoryDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Language for the keywords and categories in the response |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CategoryDataList](../../doc/models/category-data-list.md).

## Example Usage

```go
ctx := context.Background()

language := models.LanguageEnum_ES

apiResponse, err := videosController.ListVideoCategories(ctx, &language)
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


# Get Video Collection List

This endpoint lists your collections of videos and their basic attributes.

```go
GetVideoCollectionList(
    ctx context.Context,
    page *int,
    perPage *int,
    embed []models.EmbedEnum) (
    models.ApiResponse[models.CollectionDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `100`<br><br>**Constraints**: `>= 1`, `<= 150` |
| `embed` | [`[]models.EmbedEnum`](../../doc/models/embed-enum.md) | Query, Optional | Which sharing information to include in the response, such as a URL to the collection |

## Requires scope

### customer_accessCode

`collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionDataList](../../doc/models/collection-data-list.md).

## Example Usage

```go
ctx := context.Background()

page := 1

perPage := 100

apiResponse, err := videosController.GetVideoCollectionList(ctx, &page, &perPage, nil)
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


# Create Video Collection

This endpoint creates one or more collections (clipboxes). To add videos to collections, use `POST /v2/videos/collections/{id}/items`.

```go
CreateVideoCollection(
    ctx context.Context,
    body models.CollectionCreateRequest) (
    models.ApiResponse[models.CollectionCreateResponse],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.CollectionCreateRequest`](../../doc/models/collection-create-request.md) | Body, Required | Collection metadata |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**201**: Successfully created video collection

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionCreateResponse](../../doc/models/collection-create-response.md).

## Example Usage

```go
ctx := context.Background()

body := models.CollectionCreateRequest{
    Name:                 "Test Collection 19cf",
}

apiResponse, err := videosController.CreateVideoCollection(ctx, body)
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


# Get Featured Video Collection List

This endpoint lists featured video collections and a name and cover video for each collection.

```go
GetFeaturedVideoCollectionList(
    ctx context.Context,
    embed *models.Embed3Enum) (
    models.ApiResponse[models.FeaturedCollectionDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `embed` | [`*models.Embed3Enum`](../../doc/models/embed-3-enum.md) | Query, Optional | What information to include in the response, such as a URL to the collection |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.FeaturedCollectionDataList](../../doc/models/featured-collection-data-list.md).

## Example Usage

```go
ctx := context.Background()

embed := models.Embed3Enum_SHAREURL

apiResponse, err := videosController.GetFeaturedVideoCollectionList(ctx, &embed)
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


# Get Featured Video Collection

This endpoint gets more detailed information about a featured video collection, including its cover video and timestamps for its creation and most recent update. To get the videos, use `GET /v2/videos/collections/featured/{id}/items`.

```go
GetFeaturedVideoCollection(
    ctx context.Context,
    id string,
    embed *models.Embed3Enum) (
    models.ApiResponse[models.FeaturedCollection],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Collection ID |
| `embed` | [`*models.Embed3Enum`](../../doc/models/embed-3-enum.md) | Query, Optional | What information to include in the response, such as a URL to the collection |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.FeaturedCollection](../../doc/models/featured-collection.md).

## Example Usage

```go
ctx := context.Background()

id := "136351027"

apiResponse, err := videosController.GetFeaturedVideoCollection(ctx, id, nil)
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
| 404 | Featured collection not found | `ApiError` |


# Get Featured Video Collection Items

This endpoint lists the IDs of videos in a featured collection and the date that each was added.

```go
GetFeaturedVideoCollectionItems(
    ctx context.Context,
    id string,
    page *int,
    perPage *int) (
    models.ApiResponse[models.VideoCollectionItemDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Collection ID |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `100`<br><br>**Constraints**: `>= 1`, `<= 150` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.VideoCollectionItemDataList](../../doc/models/video-collection-item-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := "136351027"

page := 1

perPage := 100

apiResponse, err := videosController.GetFeaturedVideoCollectionItems(ctx, id, &page, &perPage)
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
| 404 | Featured collection not found | `ApiError` |


# Delete Video Collection

This endpoint deletes a collection.

```go
DeleteVideoCollection(
    ctx context.Context,
    id string) (
    http.Response,
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | The ID of the collection to delete |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully deleted collection

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "17555176"

resp, err := videosController.DeleteVideoCollection(ctx, id)
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
| 404 | Collection not found | `ApiError` |


# Get Video Collection

This endpoint gets more detailed information about a collection, including the timestamp for its creation and the number of videos in it. To get the videos in collections, use GET /v2/videos/collections/{id}/items.

```go
GetVideoCollection(
    ctx context.Context,
    id string,
    embed []models.EmbedEnum,
    shareCode *string) (
    models.ApiResponse[models.Collection],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | The ID of the collection to return |
| `embed` | [`[]models.EmbedEnum`](../../doc/models/embed-enum.md) | Query, Optional | Which sharing information to include in the response, such as a URL to the collection |
| `shareCode` | `*string` | Query, Optional | Code to retrieve a shared collection |

## Requires scope

### customer_accessCode

`collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Collection](../../doc/models/collection.md).

## Example Usage

```go
ctx := context.Background()

id := "17555176"

apiResponse, err := videosController.GetVideoCollection(ctx, id, nil, nil)
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
| 404 | Collection not found | `ApiError` |


# Rename Video Collection

This endpoint sets a new name for a collection.

```go
RenameVideoCollection(
    ctx context.Context,
    id string,
    body models.CollectionUpdateRequest) (
    http.Response,
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | The ID of the collection to rename |
| `body` | [`models.CollectionUpdateRequest`](../../doc/models/collection-update-request.md) | Body, Required | The new name for the collection |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully updated collection

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "17555176"

body := models.CollectionUpdateRequest{
    Name:                 "My collection with a new name",
}

resp, err := videosController.RenameVideoCollection(ctx, id, body)
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
| 404 | Collection not found | `ApiError` |


# Delete Video Collection Items

This endpoint removes one or more videos from a collection.

```go
DeleteVideoCollectionItems(
    ctx context.Context,
    id string,
    itemId []string) (
    http.Response,
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | The ID of the Collection from which items will be deleted |
| `itemId` | `[]string` | Query, Optional | One or more video IDs to remove from the collection |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully removed collection items

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "17555176"

resp, err := videosController.DeleteVideoCollectionItems(ctx, id, nil)
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
| 404 | Collection not found | `ApiError` |


# Get Video Collection Items

This endpoint lists the IDs of videos in a collection and the date that each was added.

```go
GetVideoCollectionItems(
    ctx context.Context,
    id string,
    page *int,
    perPage *int,
    shareCode *string,
    sort *models.Sort1Enum) (
    models.ApiResponse[models.CollectionItemDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Collection ID |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `100`<br><br>**Constraints**: `>= 1`, `<= 150` |
| `shareCode` | `*string` | Query, Optional | Code to retrieve the contents of a shared collection |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort order<br><br>**Default**: `"oldest"` |

## Requires scope

### customer_accessCode

`collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionItemDataList](../../doc/models/collection-item-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := "17555176"

page := 1

perPage := 100

sort := models.Sort1Enum_OLDEST

apiResponse, err := videosController.GetVideoCollectionItems(ctx, id, &page, &perPage, nil, &sort)
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
| 404 | Collection not found | `ApiError` |


# Add Video Collection Items

This endpoint adds one or more videos to a collection by video IDs.

```go
AddVideoCollectionItems(
    ctx context.Context,
    id string,
    body models.CollectionItemRequest) (
    http.Response,
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | The ID of the collection to which items should be added |
| `body` | [`models.CollectionItemRequest`](../../doc/models/collection-item-request.md) | Body, Required | Array of video IDs to add to the collection |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully added collection items

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "17555176"

body := models.CollectionItemRequest{
    Items:                []models.CollectionItem{
        models.CollectionItem{
            Id:                   "10120264",
        },
        models.CollectionItem{
            Id:                   "24419024",
        },
    },
}

resp, err := videosController.AddVideoCollectionItems(ctx, id, body)
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
| 404 | Collection not found | `ApiError` |


# Get Video License List

This endpoint lists existing licenses.

```go
GetVideoLicenseList(
    ctx context.Context,
    videoId *string,
    license *string,
    page *int,
    perPage *int,
    sort *models.Sort1Enum,
    username *string,
    startDate *time.Time,
    endDate *time.Time,
    downloadAvailability *models.DownloadAvailabilityEnum,
    teamHistory *bool) (
    models.ApiResponse[models.DownloadHistoryDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `videoId` | `*string` | Query, Optional | Show licenses for the specified video ID<br><br>**Constraints**: *Pattern*: `^[1-9]\d*$` |
| `license` | `*string` | Query, Optional | Show videos that are available with the specified license, such as `standard` or `enhanced`; prepending a `-` sign excludes results from that license<br><br>**Constraints**: *Pattern*: `^.+$` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 200` |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort by oldest or newest videos first<br><br>**Default**: `"newest"` |
| `username` | `*string` | Query, Optional | Filter licenses by username of licensee |
| `startDate` | `*time.Time` | Query, Optional | Show licenses created on or after the specified date |
| `endDate` | `*time.Time` | Query, Optional | Show licenses created before the specified date |
| `downloadAvailability` | [`*models.DownloadAvailabilityEnum`](../../doc/models/download-availability-enum.md) | Query, Optional | Filter licenses by download availability<br><br>**Default**: `"all"` |
| `teamHistory` | `*bool` | Query, Optional | Set to true to see license history for all members of your team.<br><br>**Default**: `false` |

## Requires scope

### customer_accessCode

`licenses.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.DownloadHistoryDataList](../../doc/models/download-history-data-list.md).

## Example Usage

```go
ctx := context.Background()

videoId := "12345678"

license := "standard"

page := 1

perPage := 20

sort := models.Sort1Enum_NEWEST

username := "aUniqueUsername"

startDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

downloadAvailability := models.DownloadAvailabilityEnum_ALL

teamHistory := false

apiResponse, err := videosController.GetVideoLicenseList(ctx, &videoId, &license, &page, &perPage, &sort, &username, &startDate, &endDate, &downloadAvailability, &teamHistory)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```

## Example Response *(as JSON)*

```json
{
  "data": [
    {
      "download_time": "2018-05-24T14:26:25-04:00",
      "id": "e121",
      "is_downloadable": true,
      "license": "footage_premier",
      "metadata": {
        "customer_id": "12345",
        "geo_location": "US",
        "number_viewed": "15",
        "search_term": "dog"
      },
      "subscription_id": "s12345678",
      "user": {
        "username": "myusername"
      },
      "video": {
        "format": {
          "size": "sd"
        },
        "id": "2140697"
      }
    }
  ],
  "page": 1,
  "per_page": 20
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# License Videos

This endpoint gets licenses for one or more videos. You must specify the video IDs in the body parameter and the size and subscription ID either in the query parameter or with each video ID in the body parameter. Values in the body parameter override values in the query parameters. The download links in the response are valid for 8 hours.

```go
LicenseVideos(
    ctx context.Context,
    body models.LicenseVideoRequest,
    subscriptionId *string,
    size *models.Size9Enum,
    searchId *string) (
    models.ApiResponse[models.LicenseVideoResultDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.LicenseVideoRequest`](../../doc/models/license-video-request.md) | Body, Required | List of videos to request licenses for and information about each license transaction; these values override the defaults in the query parameters |
| `subscriptionId` | `*string` | Query, Optional | The subscription ID to use for licensing |
| `size` | [`*models.Size9Enum`](../../doc/models/size-9-enum.md) | Query, Optional | The size of the video to license<br><br>**Default**: `"web"` |
| `searchId` | `*string` | Query, Optional | The Search ID that led to this licensing event |

## Requires scope

### customer_accessCode

`licenses.create`, `purchases.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.LicenseVideoResultDataList](../../doc/models/license-video-result-data-list.md).

## Example Usage

```go
ctx := context.Background()

body := models.LicenseVideoRequest{
    Videos:               []models.LicenseVideo{
        models.LicenseVideo{
            Size:                     models.ToPointer(models.Size5Enum_HD),
            SubscriptionId:           models.ToPointer("s12345678"),
            VideoId:                  "2140697",
        },
    },
}

subscriptionId := "s12345678"

size := models.Size9Enum_WEB

apiResponse, err := videosController.LicenseVideos(ctx, body, &subscriptionId, &size, nil)
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


# Download Videos

This endpoint redownloads videos that you have already received a license for.

```go
DownloadVideos(
    ctx context.Context,
    id string,
    body models.RedownloadVideo) (
    models.ApiResponse[models.Url],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | The license ID of the item to (re)download. The download links in the response are valid for 8 hours. |
| `body` | [`models.RedownloadVideo`](../../doc/models/redownload-video.md) | Body, Required | Information about the videos to redownload |

## Requires scope

### customer_accessCode

`licenses.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Url](../../doc/models/url.md).

## Example Usage

```go
ctx := context.Background()

id := "e123"

body := models.RedownloadVideo{
}

apiResponse, err := videosController.DownloadVideos(ctx, id, body)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```

## Example Response *(as JSON)*

```json
{
  "url": "https://download1.shutterstock.com/gatekeeper/W3siZSI6MTUzMzMzMzUzMCwiayI6InZpZGVvLzM5NjU4ODEvaGQubW92IiwibSI6MSwiZCI6InNodXR0ZXJzdG9jay1tZWRpYSJ9LCJjZ2lvRU14T09hNWZGTHZsN21iTWVPRVQ3MFEiXQ/shutterstock_v3965881.mov"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# Search Videos

This endpoint searches for videos. If you specify more than one search parameter, the API uses an AND condition. Array parameters can be specified multiple times; in this case, the API uses an AND or an OR condition with those values, depending on the parameter. You can also filter search terms out in the `query` parameter by prefixing the term with NOT.

```go
SearchVideos(
    ctx context.Context,
    addedDate *time.Time,
    addedDateStart *time.Time,
    addedDateEnd *time.Time,
    aspectRatio *models.AspectRatioEnum,
    category *string,
    contributor []string,
    contributorCountry []string,
    duration *int,
    durationFrom *int,
    durationTo *int,
    fps *float64,
    fpsFrom *float64,
    fpsTo *float64,
    keywordSafeSearch *bool,
    language *models.LanguageEnum,
    license []models.License5Enum,
    model []string,
    page *int,
    perPage *int,
    peopleAge *models.PeopleAge1Enum,
    peopleEthnicity []models.PeopleEthnicity3Enum,
    peopleGender *models.PeopleGender1Enum,
    peopleNumber *int,
    peopleModelReleased *bool,
    query *string,
    resolution *models.ResolutionEnum,
    safe *bool,
    sort *models.Sort4Enum,
    view *models.View1Enum) (
    models.ApiResponse[models.VideoSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `addedDate` | `*time.Time` | Query, Optional | Show videos added on the specified date |
| `addedDateStart` | `*time.Time` | Query, Optional | Show videos added on or after the specified date |
| `addedDateEnd` | `*time.Time` | Query, Optional | Show videos added before the specified date |
| `aspectRatio` | [`*models.AspectRatioEnum`](../../doc/models/aspect-ratio-enum.md) | Query, Optional | Show videos with the specified aspect ratio |
| `category` | `*string` | Query, Optional | Show videos with the specified Shutterstock-defined category; specify a category name or ID |
| `contributor` | `[]string` | Query, Optional | Show videos with the specified artist names or IDs |
| `contributorCountry` | `[]string` | Query, Optional | Show videos from contributors in one or more specified countries |
| `duration` | `*int` | Query, Optional | (Deprecated; use duration_from and duration_to instead) Show videos with the specified duration in seconds |
| `durationFrom` | `*int` | Query, Optional | Show videos with the specified duration or longer in seconds |
| `durationTo` | `*int` | Query, Optional | Show videos with the specified duration or shorter in seconds |
| `fps` | `*float64` | Query, Optional | (Deprecated; use fps_from and fps_to instead) Show videos with the specified frames per second |
| `fpsFrom` | `*float64` | Query, Optional | Show videos with the specified frames per second or more |
| `fpsTo` | `*float64` | Query, Optional | Show videos with the specified frames per second or fewer |
| `keywordSafeSearch` | `*bool` | Query, Optional | Hide results with potentially unsafe keywords<br><br>**Default**: `true` |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Set query and result language (uses Accept-Language header if not set) |
| `license` | [`[]models.License5Enum`](../../doc/models/license-5-enum.md) | Query, Optional | Show only videos with the specified license or licenses |
| `model` | `[]string` | Query, Optional | Show videos with each of the specified models |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 500` |
| `peopleAge` | [`*models.PeopleAge1Enum`](../../doc/models/people-age-1-enum.md) | Query, Optional | Show videos that feature people of the specified age range |
| `peopleEthnicity` | [`[]models.PeopleEthnicity3Enum`](../../doc/models/people-ethnicity-3-enum.md) | Query, Optional | Show videos with people of the specified ethnicities |
| `peopleGender` | [`*models.PeopleGender1Enum`](../../doc/models/people-gender-1-enum.md) | Query, Optional | Show videos with people with the specified gender |
| `peopleNumber` | `*int` | Query, Optional | Show videos with the specified number of people<br><br>**Constraints**: `>= 0`, `<= 4` |
| `peopleModelReleased` | `*bool` | Query, Optional | Show only videos of people with a signed model release |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces; you can use NOT to filter out videos that match a term |
| `resolution` | [`*models.ResolutionEnum`](../../doc/models/resolution-enum.md) | Query, Optional | Show videos with the specified resolution |
| `safe` | `*bool` | Query, Optional | Enable or disable safe search<br><br>**Default**: `true` |
| `sort` | [`*models.Sort4Enum`](../../doc/models/sort-4-enum.md) | Query, Optional | Sort by one of these categories<br><br>**Default**: `"popular"` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.VideoSearchResults](../../doc/models/video-search-results.md).

## Example Usage

```go
ctx := context.Background()

addedDate := parseTime(time.RFC3339, "2020-05-29", func(err error) { log.Fatalln(err) })

addedDateStart := parseTime(time.RFC3339, "2020-05-29", func(err error) { log.Fatalln(err) })

addedDateEnd := parseTime(time.RFC3339, "2020-05-29", func(err error) { log.Fatalln(err) })

aspectRatio := models.AspectRatioEnum_ENUM43

contributor := []string{
    "contributor7",
}

durationFrom := 60

durationTo := 180

fpsFrom := float64(24)

fpsTo := float64(60)

keywordSafeSearch := true

language := models.LanguageEnum_CS

license := []models.License5Enum{
    models.License5Enum_COMMERCIAL,
    models.License5Enum_EDITORIAL,
}

model := []string{
    "442583",
    "434750",
}

page := 1

perPage := 20

peopleAge := models.PeopleAge1Enum_ENUM20S

peopleGender := models.PeopleGender1Enum_FEMALE

peopleNumber := 2

peopleModelReleased := true

query := "dogs running on the beach"

resolution := models.ResolutionEnum_ENUM4K

safe := true

sort := models.Sort4Enum_POPULAR

view := models.View1Enum_MINIMAL

apiResponse, err := videosController.SearchVideos(ctx, &addedDate, &addedDateStart, &addedDateEnd, &aspectRatio, nil, contributor, nil, nil, &durationFrom, &durationTo, nil, &fpsFrom, &fpsTo, &keywordSafeSearch, &language, license, model, &page, &perPage, &peopleAge, nil, &peopleGender, &peopleNumber, &peopleModelReleased, &query, &resolution, &safe, &sort, &view)
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
| 404 | Not found | `ApiError` |


# Get Video Suggestions

This endpoint provides autocomplete suggestions for partial search terms.

```go
GetVideoSuggestions(
    ctx context.Context,
    query string,
    limit *int) (
    models.ApiResponse[models.Suggestions],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `query` | `string` | Query, Required | Search term for which you want keyword suggestions |
| `limit` | `*int` | Query, Optional | Limit the number of the suggestions<br><br>**Default**: `10`<br><br>**Constraints**: `>= 1`, `<= 25` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Suggestions](../../doc/models/suggestions.md).

## Example Usage

```go
ctx := context.Background()

query := "cats"

limit := 10

apiResponse, err := videosController.GetVideoSuggestions(ctx, query, &limit)
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


# Get Updated Videos

This endpoint lists videos that have been updated in the specified time period to update content management systems (CMS) or digital asset management (DAM) systems. In most cases, use the `interval` parameter to show videos that were updated recently, but you can also use the `start_date` and `end_date` parameters to specify a range of no more than three days. Do not use the `interval` parameter with either `start_date` or `end_date`.

```go
GetUpdatedVideos(
    ctx context.Context,
    startDate *time.Time,
    endDate *time.Time,
    interval *string,
    page *int,
    perPage *int,
    sort *models.Sort1Enum) (
    models.ApiResponse[models.UpdatedMediaDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `startDate` | `*time.Time` | Query, Optional | Show videos updated on or after the specified date |
| `endDate` | `*time.Time` | Query, Optional | Show videos updated before the specified date |
| `interval` | `*string` | Query, Optional | Show videos updated in the specified time period, where the time period is an interval (like SQL INTERVAL) such as 1 DAY, 6 HOUR, or 30 MINUTE; the default is 1 HOUR, which shows videos that were updated in the hour preceding the request<br><br>**Default**: `"1 HOUR"` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `100`<br><br>**Constraints**: `>= 1`, `<= 2000` |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort by oldest or newest videos first<br><br>**Default**: `"newest"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.UpdatedMediaDataList](../../doc/models/updated-media-data-list.md).

## Example Usage

```go
ctx := context.Background()

startDate := parseTime(time.RFC3339, "2020-05-29", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "2021-05-29", func(err error) { log.Fatalln(err) })

interval := "1 HOUR"

page := 1

perPage := 100

sort := models.Sort1Enum_NEWEST

apiResponse, err := videosController.GetUpdatedVideos(ctx, &startDate, &endDate, &interval, &page, &perPage, &sort)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Get Video

This endpoint shows information about a video, including URLs to previews and the sizes that it is available in.

```go
GetVideo(
    ctx context.Context,
    id string,
    language *models.LanguageEnum,
    view *models.View1Enum,
    searchId *string) (
    models.ApiResponse[models.Video],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Video ID |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Language for the keywords and categories in the response |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"full"` |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Video](../../doc/models/video.md).

## Example Usage

```go
ctx := context.Background()

id := "639703"

language := models.LanguageEnum_ES

view := models.View1Enum_FULL

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := videosController.GetVideo(ctx, id, &language, &view, &searchId)
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
| 404 | Not found | `ApiError` |


# Find Similar Videos

This endpoint searches for videos that are similar to a video that you specify.

```go
FindSimilarVideos(
    ctx context.Context,
    id string,
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
| `id` | `string` | Template, Required | The ID of a video for which similar videos should be returned |
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

id := "2140697"

language := models.LanguageEnum_ES

page := 1

perPage := 20

view := models.View1Enum_MINIMAL

apiResponse, err := videosController.FindSimilarVideos(ctx, id, &language, &page, &perPage, &view)
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

