# Editorial Images

```go
editorialImagesController := client.EditorialImagesController()
```

## Class Name

`EditorialImagesController`

## Methods

* [Get Editorial Categories](../../doc/controllers/editorial-images.md#get-editorial-categories)
* [List Editorial Image Categories](../../doc/controllers/editorial-images.md#list-editorial-image-categories)
* [Get Editorial Image License List](../../doc/controllers/editorial-images.md#get-editorial-image-license-list)
* [License Editorial Images](../../doc/controllers/editorial-images.md#license-editorial-images)
* [Get Editorial Image Livefeed List](../../doc/controllers/editorial-images.md#get-editorial-image-livefeed-list)
* [Get Editorial Image Livefeed](../../doc/controllers/editorial-images.md#get-editorial-image-livefeed)
* [Get Editorial Image Livefeed Items](../../doc/controllers/editorial-images.md#get-editorial-image-livefeed-items)
* [Search Editorial Images](../../doc/controllers/editorial-images.md#search-editorial-images)
* [Get Updated Editorial Images](../../doc/controllers/editorial-images.md#get-updated-editorial-images)
* [Get Editorial Image](../../doc/controllers/editorial-images.md#get-editorial-image)
* [License Editorial Image](../../doc/controllers/editorial-images.md#license-editorial-image)
* [Get Editorial Livefeed List](../../doc/controllers/editorial-images.md#get-editorial-livefeed-list)
* [Get Editorial Livefeed](../../doc/controllers/editorial-images.md#get-editorial-livefeed)
* [Get Editorial Livefeed Items](../../doc/controllers/editorial-images.md#get-editorial-livefeed-items)
* [Search Editorial](../../doc/controllers/editorial-images.md#search-editorial)
* [Get Updated Editorial Image](../../doc/controllers/editorial-images.md#get-updated-editorial-image)
* [Deprecated Get Editorial Content Details](../../doc/controllers/editorial-images.md#deprecated-get-editorial-content-details)


# Get Editorial Categories

**This endpoint is deprecated.**

Deprecated; use `GET /v2/editorial/images/categories` instead. This endpoint lists the categories that editorial images can belong to, which are separate from the categories that other types of assets can belong to.

```go
GetEditorialCategories(
    ctx context.Context) (
    models.ApiResponse[models.EditorialCategoryResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialCategoryResults](../../doc/models/editorial-category-results.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := editorialImagesController.GetEditorialCategories(ctx)
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


# List Editorial Image Categories

This endpoint lists the categories that editorial images can belong to, which are separate from the categories that other types of assets can belong to.

```go
ListEditorialImageCategories(
    ctx context.Context) (
    models.ApiResponse[models.EditorialImageCategoryResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialImageCategoryResults](../../doc/models/editorial-image-category-results.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := editorialImagesController.ListEditorialImageCategories(ctx)
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


# Get Editorial Image License List

This endpoint lists existing editorial image licenses.

```go
GetEditorialImageLicenseList(
    ctx context.Context,
    imageId *string,
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
| `imageId` | `*string` | Query, Optional | Show licenses for the specified editorial image ID |
| `license` | `*string` | Query, Optional | Show editorial images that are available with the specified license name |
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

imageId := "12345678"

license := "premier_editorial_all_digital"

page := 1

perPage := 20

sort := models.Sort1Enum_NEWEST

username := "aUniqueUsername"

startDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

downloadAvailability := models.DownloadAvailabilityEnum_ALL

teamHistory := false

apiResponse, err := editorialImagesController.GetEditorialImageLicenseList(ctx, &imageId, &license, &page, &perPage, &sort, &username, &startDate, &endDate, &downloadAvailability, &teamHistory)
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


# License Editorial Images

This endpoint gets licenses for one or more editorial images. You must specify the country and one or more editorial images to license. The download links in the response are valid for 8 hours.

```go
LicenseEditorialImages(
    ctx context.Context,
    body models.LicenseEditorialContentRequest) (
    models.ApiResponse[models.LicenseEditorialContentResults],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.LicenseEditorialContentRequest`](../../doc/models/license-editorial-content-request.md) | Body, Required | License editorial content |

## Requires scope

### customer_accessCode

`licenses.create`, `purchases.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.LicenseEditorialContentResults](../../doc/models/license-editorial-content-results.md).

## Example Usage

```go
ctx := context.Background()

body := models.LicenseEditorialContentRequest{
    Country:              models.ISOCountryCodeContainer.FromISOCountryCode(models.ISOCountryCodeEnum_USA),
    Editorial:            []models.LicenseEditorialContent{
        models.LicenseEditorialContent{
            EditorialId:          "10687730b",
            License:              "premier_editorial_comp",
            Metadata:             models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
            Size:                 models.ToPointer(models.SizeEnum_ORIGINAL),
        },
    },
}

apiResponse, err := editorialImagesController.LicenseEditorialImages(ctx, body)
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


# Get Editorial Image Livefeed List

```go
GetEditorialImageLivefeedList(
    ctx context.Context,
    country string,
    page *int,
    perPage *int) (
    models.ApiResponse[models.EditorialImageLivefeedList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `country` | `string` | Query, Required | Returns only livefeeds that are available for distribution in a certain country |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialImageLivefeedList](../../doc/models/editorial-image-livefeed-list.md).

## Example Usage

```go
ctx := context.Background()

country := "USA"

page := 1

perPage := 20

apiResponse, err := editorialImagesController.GetEditorialImageLivefeedList(ctx, country, &page, &perPage)
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
| 404 | Not Found | `ApiError` |


# Get Editorial Image Livefeed

```go
GetEditorialImageLivefeed(
    ctx context.Context,
    id string,
    country string) (
    models.ApiResponse[models.EditorialImageLivefeed],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Editorial livefeed ID; must be an URI encoded string |
| `country` | `string` | Query, Required | Returns only if the livefeed is available for distribution in a certain country |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialImageLivefeed](../../doc/models/editorial-image-livefeed.md).

## Example Usage

```go
ctx := context.Background()

id := "2018%2F10%2F15%2FWomen%20of%20the%20Year%20Lunch%20%26%20Awards%2C%20London"

country := "USA"

apiResponse, err := editorialImagesController.GetEditorialImageLivefeed(ctx, id, country)
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
| 404 | Not Found | `ApiError` |


# Get Editorial Image Livefeed Items

```go
GetEditorialImageLivefeedItems(
    ctx context.Context,
    id string,
    country string) (
    models.ApiResponse[models.EditorialImageContentDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Editorial livefeed ID; must be an URI encoded string |
| `country` | `string` | Query, Required | Returns only if the livefeed items are available for distribution in a certain country |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialImageContentDataList](../../doc/models/editorial-image-content-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := "2018%2F10%2F15%2FWomen%20of%20the%20Year%20Lunch%20%26%20Awards%2C%20London"

country := "USA"

apiResponse, err := editorialImagesController.GetEditorialImageLivefeedItems(ctx, id, country)
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
| 404 | Not Found | `ApiError` |


# Search Editorial Images

This endpoint searches for editorial images. If you specify more than one search parameter, the API uses an AND condition. For example, if you set the `category` parameter to "Alone,Performing" and also specify a `query` parameter, the results include only images that match the query and are in both the Alone and Performing categories. You can also filter search terms out in the `query` parameter by prefixing the term with NOT.

```go
SearchEditorialImages(
    ctx context.Context,
    country string,
    query *string,
    sort *models.Sort10Enum,
    category *string,
    supplierCode []string,
    dateStart *time.Time,
    dateEnd *time.Time,
    perPage *int,
    cursor *string) (
    models.ApiResponse[models.EditorialSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `country` | `string` | Query, Required | Show only editorial content that is available for distribution in a certain country |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces |
| `sort` | [`*models.Sort10Enum`](../../doc/models/sort-10-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"relevant"` |
| `category` | `*string` | Query, Optional | Show editorial content with each of the specified editorial categories; specify category names in a comma-separated list |
| `supplierCode` | `[]string` | Query, Optional | Show only editorial content from certain suppliers |
| `dateStart` | `*time.Time` | Query, Optional | Show only editorial content generated on or after a specific date |
| `dateEnd` | `*time.Time` | Query, Optional | Show only editorial content generated on or before a specific date |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `cursor` | `*string` | Query, Optional | The cursor of the page with which to start fetching results; this cursor is returned from previous requests |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialSearchResults](../../doc/models/editorial-search-results.md).

## Example Usage

```go
ctx := context.Background()

country := "USA"

query := "The Academy Awards"

sort := models.Sort10Enum_RELEVANT

category := "Alone,Performing"

dateStart := parseTime(time.RFC3339, "2020-05-29", func(err error) { log.Fatalln(err) })

dateEnd := parseTime(time.RFC3339, "2021-05-29", func(err error) { log.Fatalln(err) })

perPage := 20

cursor := "eyJ2IjoxLCJzIjoxfQ=="

apiResponse, err := editorialImagesController.SearchEditorialImages(ctx, country, &query, &sort, &category, nil, &dateStart, &dateEnd, &perPage, &cursor)
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


# Get Updated Editorial Images

This endpoint lists editorial images that have been updated in the specified time period to update content management systems (CMS) or digital asset management (DAM) systems. In most cases, use the date_updated_start and date_updated_end parameters to specify a range updates based on when the updates happened. You can also use the date_taken_start and date_taken_end parameters to specify a range of updates based on when the image was taken.

```go
GetUpdatedEditorialImages(
    ctx context.Context,
    mType models.Type2Enum,
    dateUpdatedStart time.Time,
    dateUpdatedEnd time.Time,
    country string,
    dateTakenStart *time.Time,
    dateTakenEnd *time.Time,
    cursor *string,
    sort *models.Sort1Enum,
    supplierCode []string,
    perPage *int) (
    models.ApiResponse[models.EditorialUpdatedResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `mType` | [`models.Type2Enum`](../../doc/models/type-2-enum.md) | Query, Required | Specify `addition` to return only images that were added or `edit` to return only images that were edited or deleted |
| `dateUpdatedStart` | `time.Time` | Query, Required | Show images images added, edited, or deleted after the specified date. Acceptable range is 1970-01-01T00:00:01 to 2038-01-19T00:00:00. |
| `dateUpdatedEnd` | `time.Time` | Query, Required | Show images images added, edited, or deleted before the specified date. Acceptable range is 1970-01-01T00:00:01 to 2038-01-19T00:00:00. |
| `country` | `string` | Query, Required | Show only editorial content that is available for distribution in a certain country |
| `dateTakenStart` | `*time.Time` | Query, Optional | Show images that were taken on or after the specified date; use this parameter if you want recently created images from the collection instead of updated older assets |
| `dateTakenEnd` | `*time.Time` | Query, Optional | Show images that were taken before the specified date |
| `cursor` | `*string` | Query, Optional | The cursor of the page with which to start fetching results; this cursor is returned from previous requests |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"newest"` |
| `supplierCode` | `[]string` | Query, Optional | Show only editorial content from certain suppliers<br><br>**Constraints**: *Maximum Length*: `5` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `500`<br><br>**Constraints**: `>= 100`, `<= 500` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialUpdatedResults](../../doc/models/editorial-updated-results.md).

## Example Usage

```go
ctx := context.Background()

mType := models.Type2Enum_EDIT

dateUpdatedStart := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

dateUpdatedEnd := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

country := "USA"

dateTakenStart := parseTime(time.RFC3339, "2020-02-04", func(err error) { log.Fatalln(err) })

dateTakenEnd := parseTime(time.RFC3339, "2020-02-05", func(err error) { log.Fatalln(err) })

cursor := "eyJ2IjoxLCJzIjoyfQ=="

sort := models.Sort1Enum_NEWEST

perPage := 200

apiResponse, err := editorialImagesController.GetUpdatedEditorialImages(ctx, mType, dateUpdatedStart, dateUpdatedEnd, country, &dateTakenStart, &dateTakenEnd, &cursor, &sort, nil, &perPage)
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


# Get Editorial Image

This endpoint shows information about an editorial image, including a URL to a preview image and the sizes that it is available in.

```go
GetEditorialImage(
    ctx context.Context,
    id string,
    country string) (
    models.ApiResponse[models.EditorialContent],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Editorial ID |
| `country` | `string` | Query, Required | Returns only if the content is available for distribution in a certain country |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialContent](../../doc/models/editorial-content.md).

## Example Usage

```go
ctx := context.Background()

id := "9926131a"

country := "USA"

apiResponse, err := editorialImagesController.GetEditorialImage(ctx, id, country)
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
| 404 | Not Found | `ApiError` |


# License Editorial Image

**This endpoint is deprecated.**

Deprecated; use `POST /v2/editorial/images/licenses` instead to get licenses for one or more editorial images. You must specify the country and one or more editorial images to license. The download links in the response are valid for 8 hours.

```go
LicenseEditorialImage(
    ctx context.Context,
    body models.LicenseEditorialContentRequest) (
    models.ApiResponse[models.LicenseEditorialContentResults],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.LicenseEditorialContentRequest`](../../doc/models/license-editorial-content-request.md) | Body, Required | License editorial content |

## Requires scope

### customer_accessCode

`licenses.create`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.LicenseEditorialContentResults](../../doc/models/license-editorial-content-results.md).

## Example Usage

```go
ctx := context.Background()

body := models.LicenseEditorialContentRequest{
    Country:              models.ISOCountryCodeContainer.FromISOCountryCode(models.ISOCountryCodeEnum_USA),
    Editorial:            []models.LicenseEditorialContent{
        models.LicenseEditorialContent{
            EditorialId:          "10687730b",
            License:              "premier_editorial_comp",
            Metadata:             models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
            Size:                 models.ToPointer(models.SizeEnum_ORIGINAL),
        },
    },
}

apiResponse, err := editorialImagesController.LicenseEditorialImage(ctx, body)
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
        "url": "https://s3-eu-west-1.amazonaws.com/api-downloads.rexfeatures.com/[random-characters].jpg?Expires=1524717323"
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
| 406 | Not Acceptable | `ApiError` |


# Get Editorial Livefeed List

**This endpoint is deprecated.**

Deprecated; use `GET /v2/editorial/images/livefeeds` instead to get a list of editorial livefeeds.

```go
GetEditorialLivefeedList(
    ctx context.Context,
    country string,
    page *int,
    perPage *int) (
    models.ApiResponse[models.EditorialLivefeedList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `country` | `string` | Query, Required | Returns only livefeeds that are available for distribution in a certain country |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialLivefeedList](../../doc/models/editorial-livefeed-list.md).

## Example Usage

```go
ctx := context.Background()

country := "USA"

page := 1

perPage := 20

apiResponse, err := editorialImagesController.GetEditorialLivefeedList(ctx, country, &page, &perPage)
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


# Get Editorial Livefeed

**This endpoint is deprecated.**

Deprecated: use `GET /v2/editorial/images/livefeeds/{id}` instead to get an editorial livefeed.

```go
GetEditorialLivefeed(
    ctx context.Context,
    id string,
    country string) (
    models.ApiResponse[models.EditorialLivefeed],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Editorial livefeed ID; must be an URI encoded string |
| `country` | `string` | Query, Required | Returns only if the livefeed is available for distribution in a certain country |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialLivefeed](../../doc/models/editorial-livefeed.md).

## Example Usage

```go
ctx := context.Background()

id := "2018%2F10%2F15%2FWomen%20of%20the%20Year%20Lunch%20%26%20Awards%2C%20London"

country := "USA"

apiResponse, err := editorialImagesController.GetEditorialLivefeed(ctx, id, country)
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


# Get Editorial Livefeed Items

**This endpoint is deprecated.**

Deprecated; use `GET /v2/editorial/images/livefeeds/{id}/items` instead to get editorial livefeed items.

```go
GetEditorialLivefeedItems(
    ctx context.Context,
    id string,
    country string) (
    models.ApiResponse[models.EditorialContentDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Editorial livefeed ID; must be an URI encoded string |
| `country` | `string` | Query, Required | Returns only if the livefeed items are available for distribution in a certain country |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialContentDataList](../../doc/models/editorial-content-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := "2018%2F10%2F15%2FWomen%20of%20the%20Year%20Lunch%20%26%20Awards%2C%20London"

country := "USA"

apiResponse, err := editorialImagesController.GetEditorialLivefeedItems(ctx, id, country)
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


# Search Editorial

**This endpoint is deprecated.**

Deprecated; use `GET /v2/editorial/images/search` instead to search for editorial images.

```go
SearchEditorial(
    ctx context.Context,
    country string,
    query *string,
    sort *models.Sort10Enum,
    category *string,
    supplierCode []string,
    dateStart *time.Time,
    dateEnd *time.Time,
    perPage *int,
    cursor *string) (
    models.ApiResponse[models.EditorialSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `country` | `string` | Query, Required | Show only editorial content that is available for distribution in a certain country |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces |
| `sort` | [`*models.Sort10Enum`](../../doc/models/sort-10-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"relevant"` |
| `category` | `*string` | Query, Optional | Show editorial content within a certain editorial category; specify by category name |
| `supplierCode` | `[]string` | Query, Optional | Show only editorial content from certain suppliers |
| `dateStart` | `*time.Time` | Query, Optional | Show only editorial content generated on or after a specific date |
| `dateEnd` | `*time.Time` | Query, Optional | Show only editorial content generated on or before a specific date |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `cursor` | `*string` | Query, Optional | The cursor of the page with which to start fetching results; this cursor is returned from previous requests |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialSearchResults](../../doc/models/editorial-search-results.md).

## Example Usage

```go
ctx := context.Background()

country := "USA"

sort := models.Sort10Enum_RELEVANT

perPage := 20

apiResponse, err := editorialImagesController.SearchEditorial(ctx, country, nil, &sort, nil, nil, nil, nil, &perPage, nil)
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


# Get Updated Editorial Image

**This endpoint is deprecated.**

Deprecated; use `GET /v2/editorial/images/updated` instead to get recently updated items.

```go
GetUpdatedEditorialImage(
    ctx context.Context,
    mType models.Type2Enum,
    dateUpdatedStart time.Time,
    dateUpdatedEnd time.Time,
    country string,
    dateTakenStart *time.Time,
    dateTakenEnd *time.Time,
    cursor *string,
    sort *models.Sort1Enum,
    supplierCode []string,
    perPage *int) (
    models.ApiResponse[models.EditorialUpdatedResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `mType` | [`models.Type2Enum`](../../doc/models/type-2-enum.md) | Query, Required | Specify `addition` to return only images that were added or `edit` to return only images that were edited or deleted |
| `dateUpdatedStart` | `time.Time` | Query, Required | Show images images added, edited, or deleted after the specified date. Acceptable range is 1970-01-01T00:00:01 to 2038-01-19T00:00:00. |
| `dateUpdatedEnd` | `time.Time` | Query, Required | Show images images added, edited, or deleted before the specified date. Acceptable range is 1970-01-01T00:00:01 to 2038-01-19T00:00:00. |
| `country` | `string` | Query, Required | Show only editorial content that is available for distribution in a certain country |
| `dateTakenStart` | `*time.Time` | Query, Optional | Show images that were taken on or after the specified date; use this parameter if you want recently created images from the collection instead of updated older assets |
| `dateTakenEnd` | `*time.Time` | Query, Optional | Show images that were taken before the specified date |
| `cursor` | `*string` | Query, Optional | The cursor of the page with which to start fetching results; this cursor is returned from previous requests |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"newest"` |
| `supplierCode` | `[]string` | Query, Optional | Show only editorial content from certain suppliers<br><br>**Constraints**: *Maximum Length*: `5` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `500`<br><br>**Constraints**: `>= 100`, `<= 500` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialUpdatedResults](../../doc/models/editorial-updated-results.md).

## Example Usage

```go
ctx := context.Background()

mType := models.Type2Enum_EDIT

dateUpdatedStart := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

dateUpdatedEnd := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

country := "USA"

dateTakenStart := parseTime(time.RFC3339, "2020-02-04", func(err error) { log.Fatalln(err) })

dateTakenEnd := parseTime(time.RFC3339, "2020-02-05", func(err error) { log.Fatalln(err) })

cursor := "eyJ2IjoxLCJzIjoyfQ=="

sort := models.Sort1Enum_NEWEST

perPage := 200

apiResponse, err := editorialImagesController.GetUpdatedEditorialImage(ctx, mType, dateUpdatedStart, dateUpdatedEnd, country, &dateTakenStart, &dateTakenEnd, &cursor, &sort, nil, &perPage)
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


# Deprecated Get Editorial Content Details

**This endpoint is deprecated.**

Deprecated; use `GET /v2/editorial/images/{id}` instead to show information about an editorial image, including a URL to a preview image and the sizes that it is available in.

```go
DeprecatedGetEditorialContentDetails(
    ctx context.Context,
    id string,
    country string,
    searchId *string) (
    models.ApiResponse[models.EditorialContent],
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

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.EditorialContent](../../doc/models/editorial-content.md).

## Example Usage

```go
ctx := context.Background()

id := "9926131a"

country := "USA"

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := editorialImagesController.DeprecatedGetEditorialContentDetails(ctx, id, country, &searchId)
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
| 404 | Not Found | `ApiError` |

