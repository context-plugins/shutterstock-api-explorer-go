# Editorial Video

```go
editorialVideoController := client.EditorialVideoController()
```

## Class Name

`EditorialVideoController`

## Methods

* [List Editorial Video Categories](../../doc/controllers/editorial-video.md#list-editorial-video-categories)
* [Get Editorial Video License List](../../doc/controllers/editorial-video.md#get-editorial-video-license-list)
* [License Editorial Video](../../doc/controllers/editorial-video.md#license-editorial-video)
* [Search Editorial Videos](../../doc/controllers/editorial-video.md#search-editorial-videos)
* [Get Editorial Video](../../doc/controllers/editorial-video.md#get-editorial-video)


# List Editorial Video Categories

This endpoint lists the categories that editorial videos can belong to, which are separate from the categories that other types of assets can belong to.

```go
ListEditorialVideoCategories(
    ctx context.Context) (
    models.ApiResponse[models.EditorialVideoCategoryResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialVideoCategoryResults](../../doc/models/editorial-video-category-results.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := editorialVideoController.ListEditorialVideoCategories(ctx)
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


# Get Editorial Video License List

This endpoint lists existing editorial video licenses.

```go
GetEditorialVideoLicenseList(
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
| `videoId` | `*string` | Query, Optional | Show licenses for the specified editorial video ID |
| `license` | `*string` | Query, Optional | Show editorial videos that are available with the specified license name |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 200` |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort order<br><br>**Default**: `"newest"` |
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

license := "premier_editorial_all_media"

page := 1

perPage := 20

sort := models.Sort1Enum_NEWEST

username := "aUniqueUsername"

startDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

downloadAvailability := models.DownloadAvailabilityEnum_ALL

teamHistory := false

apiResponse, err := editorialVideoController.GetEditorialVideoLicenseList(ctx, &videoId, &license, &page, &perPage, &sort, &username, &startDate, &endDate, &downloadAvailability, &teamHistory)
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
      "download_time": "2020-12-18T02:22:56.000Z",
      "id": "e1dbb15d5384725d292cf64f793ac45062",
      "is_downloadable": false,
      "license": "premier_editorial_all_digital",
      "metadata": {
        "client": "Company A",
        "job": "Important project",
        "other": "Important media",
        "purchase_order": "457234"
      },
      "subscription_id": "s12345678",
      "user": {
        "username": "username1"
      },
      "video": {
        "format": {
          "size": "original"
        },
        "id": "11231389im"
      }
    },
    {
      "download_time": "2020-12-11T01:24:22.000Z",
      "id": "e1dbb15d5384725d292cf64f793ac45114",
      "is_downloadable": false,
      "license": "premier_editorial_all_digital",
      "metadata": {
        "client": "Company B",
        "job": "Important project",
        "other": "Important image",
        "purchase_order": "5583831"
      },
      "subscription_id": "s12345678",
      "user": {
        "username": "username2"
      },
      "video": {
        "format": {
          "size": "original"
        },
        "id": "11231442aa"
      }
    }
  ],
  "page": 1,
  "per_page": 2
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# License Editorial Video

This endpoint gets licenses for one or more editorial videos. You must specify the country and one or more editorial videos to license. The download links in the response are valid for 8 hours.

```go
LicenseEditorialVideo(
    ctx context.Context,
    body models.LicenseEditorialVideoContentRequest) (
    models.ApiResponse[models.LicenseEditorialContentResults],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.LicenseEditorialVideoContentRequest`](../../doc/models/license-editorial-video-content-request.md) | Body, Required | License editorial video content |

## Requires scope

### customer_accessCode

`licenses.create`, `purchases.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.LicenseEditorialContentResults](../../doc/models/license-editorial-content-results.md).

## Example Usage

```go
ctx := context.Background()

body := models.LicenseEditorialVideoContentRequest{
    Country:              models.ISOCountryCodeContainer.FromISOCountryCode(models.ISOCountryCodeEnum_USA),
    Editorial:            []models.LicenseEditorialVideoContent{
        models.LicenseEditorialVideoContent{
            EditorialId:          "10679854a",
            License:              models.License2Enum_PREMIEREDITORIALVIDEODIGITALONLY,
            Metadata:             models.ToPointer(interface{}("[purchase_order, 12345]")),
            Size:                 models.ToPointer(models.Size1Enum_ORIGINAL),
        },
    },
}

apiResponse, err := editorialVideoController.LicenseEditorialVideo(ctx, body)
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
      "download": {
        "url": "https://s3-eu-west-1.amazonaws.com/api-downloads.rexfeatures.com/[random-characters].mov?Expires=1524717323"
      },
      "editorial_id": "69656358"
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# Search Editorial Videos

This endpoint searches for editorial videos. If you specify more than one search parameter, the API uses an AND condition. For example, if you set the `category` parameter to "Alone,Performing" and also specify a `query` parameter, the results include only videos that match the query and are in both the Alone and Performing categories.  You can also filter search terms out in the `query` parameter by prefixing the term with NOT.

```go
SearchEditorialVideos(
    ctx context.Context,
    country string,
    query *string,
    sort *models.Sort10Enum,
    category *string,
    supplierCode []string,
    dateStart *time.Time,
    dateEnd *time.Time,
    resolution *models.ResolutionEnum,
    fps *float64,
    perPage *int,
    cursor *string) (
    models.ApiResponse[models.EditorialVideoSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `country` | `string` | Query, Required | Show only editorial video content that is available for distribution in a certain country |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces |
| `sort` | [`*models.Sort10Enum`](../../doc/models/sort-10-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"relevant"` |
| `category` | `*string` | Query, Optional | Show editorial content with each of the specified editorial categories; specify category names in a comma-separated list |
| `supplierCode` | `[]string` | Query, Optional | Show only editorial video content from certain suppliers |
| `dateStart` | `*time.Time` | Query, Optional | Show only editorial video content generated on or after a specific date |
| `dateEnd` | `*time.Time` | Query, Optional | Show only editorial video content generated on or before a specific date |
| `resolution` | [`*models.ResolutionEnum`](../../doc/models/resolution-enum.md) | Query, Optional | Show only editorial video content with specific resolution |
| `fps` | `*float64` | Query, Optional | Show only editorial video content generated with specific frames per second |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `cursor` | `*string` | Query, Optional | The cursor of the page with which to start fetching results; this cursor is returned from previous requests |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialVideoSearchResults](../../doc/models/editorial-video-search-results.md).

## Example Usage

```go
ctx := context.Background()

country := "USA"

query := "The Academy Awards"

sort := models.Sort10Enum_RELEVANT

category := "Alone,Performing"

dateStart := parseTime(time.RFC3339, "2020-05-29", func(err error) { log.Fatalln(err) })

dateEnd := parseTime(time.RFC3339, "2021-05-29", func(err error) { log.Fatalln(err) })

resolution := models.ResolutionEnum_ENUM4K

fps := float64(24)

perPage := 20

cursor := "eyJ2IjoxLCJzIjoxfQ=="

apiResponse, err := editorialVideoController.SearchEditorialVideos(ctx, country, &query, &sort, &category, nil, &dateStart, &dateEnd, &resolution, &fps, &perPage, &cursor)
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
| 406 | Not Acceptable | `ApiError` |


# Get Editorial Video

This endpoint shows information about an editorial image, including a URL to a preview image and the sizes that it is available in.

```go
GetEditorialVideo(
    ctx context.Context,
    id string,
    country string,
    searchId *string) (
    models.ApiResponse[models.EditorialVideoContent],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Editorial ID |
| `country` | `string` | Query, Required | Returns only if the content is available for distribution in a certain country |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialVideoContent](../../doc/models/editorial-video-content.md).

## Example Usage

```go
ctx := context.Background()

id := "9926131a"

country := "USA"

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := editorialVideoController.GetEditorialVideo(ctx, id, country, &searchId)
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
| 406 | Not Acceptable | `ApiError` |

