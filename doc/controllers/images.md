# Images

```go
imagesController := client.ImagesController()
```

## Class Name

`ImagesController`

## Methods

* [Bulk Search Images](../../doc/controllers/images.md#bulk-search-images)
* [Get Image List](../../doc/controllers/images.md#get-image-list)
* [List Image Categories](../../doc/controllers/images.md#list-image-categories)
* [Get Image Collection List](../../doc/controllers/images.md#get-image-collection-list)
* [Create Image Collection](../../doc/controllers/images.md#create-image-collection)
* [Get Featured Image Collection List](../../doc/controllers/images.md#get-featured-image-collection-list)
* [Get Featured Image Collection](../../doc/controllers/images.md#get-featured-image-collection)
* [Get Featured Image Collection Items](../../doc/controllers/images.md#get-featured-image-collection-items)
* [Delete Image Collection](../../doc/controllers/images.md#delete-image-collection)
* [Get Image Collection](../../doc/controllers/images.md#get-image-collection)
* [Rename Image Collection](../../doc/controllers/images.md#rename-image-collection)
* [Delete Image Collection Items](../../doc/controllers/images.md#delete-image-collection-items)
* [Get Image Collection Items](../../doc/controllers/images.md#get-image-collection-items)
* [Add Image Collection Items](../../doc/controllers/images.md#add-image-collection-items)
* [Get Image License List](../../doc/controllers/images.md#get-image-license-list)
* [License Images](../../doc/controllers/images.md#license-images)
* [Download Image](../../doc/controllers/images.md#download-image)
* [Get Image Recommendations](../../doc/controllers/images.md#get-image-recommendations)
* [Search Images](../../doc/controllers/images.md#search-images)
* [Get Image Suggestions](../../doc/controllers/images.md#get-image-suggestions)
* [Get Image Keyword Suggestions](../../doc/controllers/images.md#get-image-keyword-suggestions)
* [Get Updated Images](../../doc/controllers/images.md#get-updated-images)
* [Get Image](../../doc/controllers/images.md#get-image)
* [List Similar Images](../../doc/controllers/images.md#list-similar-images)


# Bulk Search Images

This endpoint runs up to 5 image searches in a single request and returns up to 20 results per search. You can provide global search parameters in the query parameters and override them for each search in the body parameter. The query and body parameters are the same as in the `GET /v2/images/search` endpoint.

```go
BulkSearchImages(
    ctx context.Context,
    body []models.SearchImage,
    addedDate *time.Time,
    addedDateStart *time.Time,
    aspectRatioMin *float64,
    aspectRatioMax *float64,
    aspectRatio *float64,
    addedDateEnd *time.Time,
    category *string,
    color *string,
    contributor []string,
    contributorCountry *models.BulkSearchImagesContributorCountry,
    fields *string,
    height *int,
    heightFrom *int,
    heightTo *int,
    imageType []models.ImageType1Enum,
    keywordSafeSearch *bool,
    language *models.LanguageEnum,
    license []models.LicenseEnum,
    model []string,
    orientation *models.Orientation1Enum,
    page *int,
    perPage *int,
    peopleModelReleased *bool,
    peopleAge *models.PeopleAge1Enum,
    peopleEthnicity []models.PeopleEthnicity1Enum,
    peopleGender *models.PeopleGender1Enum,
    peopleNumber *int,
    region *models.BulkSearchImagesRegion,
    safe *bool,
    sort *models.Sort4Enum,
    spellcheckQuery *bool,
    view *models.View1Enum,
    width *int,
    widthFrom *int,
    widthTo *int) (
    models.ApiResponse[models.BulkImageSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`[]models.SearchImage`](../../doc/models/search-image.md) | Body, Required | List of queries to request results for and filters to apply per query; these values override the defaults in the query parameters<br><br>**Constraints**: *Maximum Items*: `5` |
| `addedDate` | `*time.Time` | Query, Optional | Show images added on the specified date |
| `addedDateStart` | `*time.Time` | Query, Optional | Show images added on or after the specified date |
| `aspectRatioMin` | `*float64` | Query, Optional | Show images with the specified aspect ratio or higher, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `> 0` |
| `aspectRatioMax` | `*float64` | Query, Optional | Show images with the specified aspect ratio or lower, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `> 0` |
| `aspectRatio` | `*float64` | Query, Optional | Show images with the specified aspect ratio, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `> 0` |
| `addedDateEnd` | `*time.Time` | Query, Optional | Show images added before the specified date |
| `category` | `*string` | Query, Optional | Show images with the specified Shutterstock-defined category; specify a category name or ID |
| `color` | `*string` | Query, Optional | Specify either a hexadecimal color in the format '4F21EA' or 'grayscale'; the API returns images that use similar colors |
| `contributor` | `[]string` | Query, Optional | Show images with the specified contributor names or IDs, allows multiple |
| `contributorCountry` | [`*models.BulkSearchImagesContributorCountry`](../../doc/models/containers/bulk-search-images-contributor-country.md) | Query, Optional | This is a container for one-of cases. |
| `fields` | `*string` | Query, Optional | Fields to display in the response; see the documentation for the fields parameter in the overview section |
| `height` | `*int` | Query, Optional | (Deprecated; use height_from and height_to instead) Show images with the specified height |
| `heightFrom` | `*int` | Query, Optional | Show images with the specified height or larger, in pixels |
| `heightTo` | `*int` | Query, Optional | Show images with the specified height or smaller, in pixels |
| `imageType` | [`[]models.ImageType1Enum`](../../doc/models/image-type-1-enum.md) | Query, Optional | Show images of the specified type |
| `keywordSafeSearch` | `*bool` | Query, Optional | Hide results with potentially unsafe keywords<br><br>**Default**: `true` |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Set query and result language (uses Accept-Language header if not set) |
| `license` | [`[]models.LicenseEnum`](../../doc/models/license-enum.md) | Query, Optional | Show only images with the specified license |
| `model` | `[]string` | Query, Optional | Show image results with the specified model IDs |
| `orientation` | [`*models.Orientation1Enum`](../../doc/models/orientation-1-enum.md) | Query, Optional | Show image results with horizontal or vertical orientation |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 20` |
| `peopleModelReleased` | `*bool` | Query, Optional | Show images of people with a signed model release |
| `peopleAge` | [`*models.PeopleAge1Enum`](../../doc/models/people-age-1-enum.md) | Query, Optional | Show images that feature people of the specified age category |
| `peopleEthnicity` | [`[]models.PeopleEthnicity1Enum`](../../doc/models/people-ethnicity-1-enum.md) | Query, Optional | Show images with people of the specified ethnicities, or start with NOT to show images without those ethnicities |
| `peopleGender` | [`*models.PeopleGender1Enum`](../../doc/models/people-gender-1-enum.md) | Query, Optional | Show images with people of the specified gender |
| `peopleNumber` | `*int` | Query, Optional | Show images with the specified number of people<br><br>**Constraints**: `>= 0`, `<= 4` |
| `region` | [`*models.BulkSearchImagesRegion`](../../doc/models/containers/bulk-search-images-region.md) | Query, Optional | This is a container for any-of cases. |
| `safe` | `*bool` | Query, Optional | Enable or disable safe search<br><br>**Default**: `true` |
| `sort` | [`*models.Sort4Enum`](../../doc/models/sort-4-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"popular"` |
| `spellcheckQuery` | `*bool` | Query, Optional | Spellcheck the search query and return results on suggested spellings<br><br>**Default**: `true` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `width` | `*int` | Query, Optional | (Deprecated; use width_from and width_to instead) Show images with the specified width |
| `widthFrom` | `*int` | Query, Optional | Show images with the specified width or larger, in pixels |
| `widthTo` | `*int` | Query, Optional | Show images with the specified width or smaller, in pixels |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.BulkImageSearchResults](../../doc/models/bulk-image-search-results.md).

## Example Usage

```go
ctx := context.Background()

body := []models.SearchImage{
    models.SearchImage{
        License:              []models.LicenseEnum{
            models.LicenseEnum_EDITORIAL,
        },
        Query:                models.ToPointer("cat"),
        Sort:                 models.ToPointer(models.SortEnum_POPULAR),
    },
}

addedDate := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

addedDateStart := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

aspectRatioMin := float64(1.7778)

aspectRatioMax := float64(1.7778)

aspectRatio := float64(1.7778)

addedDateEnd := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

color := "4F21EA"

contributor := []string{
    "123456",
}

heightFrom := 1080

heightTo := 1080

keywordSafeSearch := true

language := models.LanguageEnum_FR

model := []string{
    "12345",
    "67890",
}

orientation := models.Orientation1Enum_VERTICAL

page := 1

perPage := 10

peopleModelReleased := true

peopleAge := models.PeopleAge1Enum_ENUM20S

peopleGender := models.PeopleGender1Enum_BOTH

peopleNumber := 2

region := models.BulkSearchImagesRegionContainer.FromString("US")

safe := true

sort := models.Sort4Enum_POPULAR

spellcheckQuery := true

view := models.View1Enum_MINIMAL

widthFrom := 1920

widthTo := 1920

apiResponse, err := imagesController.BulkSearchImages(ctx, body, &addedDate, &addedDateStart, &aspectRatioMin, &aspectRatioMax, &aspectRatio, &addedDateEnd, nil, &color, contributor, nil, nil, nil, &heightFrom, &heightTo, nil, &keywordSafeSearch, &language, nil, model, &orientation, &page, &perPage, &peopleModelReleased, &peopleAge, nil, &peopleGender, &peopleNumber, &region, &safe, &sort, &spellcheckQuery, &view, nil, &widthFrom, &widthTo)
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


# Get Image List

This endpoint lists information about one or more images, including the available sizes.

```go
GetImageList(
    ctx context.Context,
    id []string,
    view *models.View1Enum,
    searchId *string) (
    models.ApiResponse[models.ImageDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Required | One or more image IDs<br><br>**Constraints**: *Maximum Items*: `500` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.ImageDataList](../../doc/models/image-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := []string{
    "1110335168",
    "465011609",
}

view := models.View1Enum_MINIMAL

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := imagesController.GetImageList(ctx, id, &view, &searchId)
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


# List Image Categories

This endpoint lists the categories (Shutterstock-assigned genres) that images can belong to.

```go
ListImageCategories(
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

apiResponse, err := imagesController.ListImageCategories(ctx, &language)
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


# Get Image Collection List

This endpoint lists your collections of images and their basic attributes.

```go
GetImageCollectionList(
    ctx context.Context,
    embed []models.EmbedEnum,
    page *int,
    perPage *int) (
    models.ApiResponse[models.CollectionDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `embed` | [`[]models.EmbedEnum`](../../doc/models/embed-enum.md) | Query, Optional | Which sharing information to include in the response, such as a URL to the collection |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `100`<br><br>**Constraints**: `>= 1`, `<= 150` |

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

perPage := 2

apiResponse, err := imagesController.GetImageCollectionList(ctx, nil, &page, &perPage)
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


# Create Image Collection

This endpoint creates one or more image collections (lightboxes). To add images to the collections, use `POST /v2/images/collections/{id}/items`.

```go
CreateImageCollection(
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
| `body` | [`models.CollectionCreateRequest`](../../doc/models/collection-create-request.md) | Body, Required | The names of the new collections |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**201**: Successfully created image collection

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionCreateResponse](../../doc/models/collection-create-response.md).

## Example Usage

```go
ctx := context.Background()

body := models.CollectionCreateRequest{
    Name:                 "Test Collection 19cf",
}

apiResponse, err := imagesController.CreateImageCollection(ctx, body)
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


# Get Featured Image Collection List

This endpoint lists featured collections of specific types and a name and cover image for each collection.

```go
GetFeaturedImageCollectionList(
    ctx context.Context,
    embed *models.Embed3Enum,
    mType []models.Type4Enum,
    assetHint *models.AssetHintEnum) (
    models.ApiResponse[models.FeaturedCollectionDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `embed` | [`*models.Embed3Enum`](../../doc/models/embed-3-enum.md) | Query, Optional | Which sharing information to include in the response, such as a URL to the collection |
| `mType` | [`[]models.Type4Enum`](../../doc/models/type-4-enum.md) | Query, Optional | The types of collections to return |
| `assetHint` | [`*models.AssetHintEnum`](../../doc/models/asset-hint-enum.md) | Query, Optional | Cover image size<br><br>**Default**: `"1x"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.FeaturedCollectionDataList](../../doc/models/featured-collection-data-list.md).

## Example Usage

```go
ctx := context.Background()

embed := models.Embed3Enum_SHAREURL

mType := []models.Type4Enum{
    models.Type4Enum_PHOTO,
}

assetHint := models.AssetHintEnum_ENUM1X

apiResponse, err := imagesController.GetFeaturedImageCollectionList(ctx, &embed, mType, &assetHint)
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


# Get Featured Image Collection

This endpoint gets more detailed information about a featured collection, including its cover image and timestamps for its creation and most recent update. To get the images, use `GET /v2/images/collections/featured/{id}/items`.

```go
GetFeaturedImageCollection(
    ctx context.Context,
    id string,
    embed *models.Embed3Enum,
    assetHint *models.AssetHintEnum) (
    models.ApiResponse[models.FeaturedCollection],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Collection ID |
| `embed` | [`*models.Embed3Enum`](../../doc/models/embed-3-enum.md) | Query, Optional | Which sharing information to include in the response, such as a URL to the collection |
| `assetHint` | [`*models.AssetHintEnum`](../../doc/models/asset-hint-enum.md) | Query, Optional | Cover image size<br><br>**Default**: `"1x"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.FeaturedCollection](../../doc/models/featured-collection.md).

## Example Usage

```go
ctx := context.Background()

id := "136351027"

assetHint := models.AssetHintEnum_ENUM1X

apiResponse, err := imagesController.GetFeaturedImageCollection(ctx, id, nil, &assetHint)
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


# Get Featured Image Collection Items

This endpoint lists the IDs of images in a featured collection and the date that each was added.

```go
GetFeaturedImageCollectionItems(
    ctx context.Context,
    id string,
    page *int,
    perPage *int) (
    models.ApiResponse[models.CollectionItemDataList],
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

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionItemDataList](../../doc/models/collection-item-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := "136351027"

page := 1

perPage := 100

apiResponse, err := imagesController.GetFeaturedImageCollectionItems(ctx, id, &page, &perPage)
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


# Delete Image Collection

This endpoint deletes an image collection.

```go
DeleteImageCollection(
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
| `id` | `string` | Template, Required | Collection ID |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully deleted collection

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "136351027"

resp, err := imagesController.DeleteImageCollection(ctx, id)
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


# Get Image Collection

This endpoint gets more detailed information about a collection, including its cover image and timestamps for its creation and most recent update. To get the images in collections, use `GET /v2/images/collections/{id}/items`.

```go
GetImageCollection(
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
| `id` | `string` | Template, Required | Collection ID |
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

id := "126351027"

apiResponse, err := imagesController.GetImageCollection(ctx, id, nil, nil)
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


# Rename Image Collection

This endpoint sets a new name for an image collection.

```go
RenameImageCollection(
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
| `id` | `string` | Template, Required | Collection ID |
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

id := "126351027"

body := models.CollectionUpdateRequest{
    Name:                 "My collection with a new name",
}

resp, err := imagesController.RenameImageCollection(ctx, id, body)
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


# Delete Image Collection Items

This endpoint removes one or more images from a collection.

```go
DeleteImageCollectionItems(
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
| `id` | `string` | Template, Required | Collection ID |
| `itemId` | `[]string` | Query, Optional | One or more image IDs to remove from the collection |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully removed collection items

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "126351027"

resp, err := imagesController.DeleteImageCollectionItems(ctx, id, nil)
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


# Get Image Collection Items

This endpoint lists the IDs of images in a collection and the date that each was added.

```go
GetImageCollectionItems(
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

id := "126351027"

page := 1

perPage := 100

sort := models.Sort1Enum_OLDEST

apiResponse, err := imagesController.GetImageCollectionItems(ctx, id, &page, &perPage, nil, &sort)
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


# Add Image Collection Items

This endpoint adds one or more images to a collection by image IDs.

```go
AddImageCollectionItems(
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
| `id` | `string` | Template, Required | Collection ID |
| `body` | [`models.CollectionItemRequest`](../../doc/models/collection-item-request.md) | Body, Required | Array of image IDs to add to the collection |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully added collection items

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "126351027"

body := models.CollectionItemRequest{
    Items:                []models.CollectionItem{
        models.CollectionItem{
            Id:                   "49572945",
        },
    },
}

resp, err := imagesController.AddImageCollectionItems(ctx, id, body)
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


# Get Image License List

This endpoint lists existing licenses.

```go
GetImageLicenseList(
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
| `imageId` | `*string` | Query, Optional | Show licenses for the specified image ID<br><br>**Constraints**: *Pattern*: `^[1-9]\d*$` |
| `license` | `*string` | Query, Optional | Show images that are available with the specified license, such as `standard` or `enhanced`; prepending a `-` sign excludes results from that license<br><br>**Constraints**: *Pattern*: `^.+$` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 200` |
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

license := "standard"

page := 1

perPage := 20

sort := models.Sort1Enum_NEWEST

username := "aUniqueUsername"

startDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

downloadAvailability := models.DownloadAvailabilityEnum_ALL

teamHistory := false

apiResponse, err := imagesController.GetImageLicenseList(ctx, &imageId, &license, &page, &perPage, &sort, &username, &startDate, &endDate, &downloadAvailability, &teamHistory)
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


# License Images

This endpoint gets licenses for one or more images. You must specify the image IDs in the body parameter and other details like the format, size, and subscription ID either in the query parameter or with each image ID in the body parameter. Values in the body parameter override values in the query parameters. The download links in the response are valid for 8 hours.

```go
LicenseImages(
    ctx context.Context,
    body models.LicenseImageRequest,
    subscriptionId *string,
    format *models.Format4Enum,
    size *models.Size8Enum,
    searchId *string) (
    models.ApiResponse[models.LicenseImageResultDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.LicenseImageRequest`](../../doc/models/license-image-request.md) | Body, Required | List of images to request licenses for and information about each license transaction; these values override the defaults in the query parameters |
| `subscriptionId` | `*string` | Query, Optional | Subscription ID to use to license the image |
| `format` | [`*models.Format4Enum`](../../doc/models/format-4-enum.md) | Query, Optional | (Deprecated) Image format |
| `size` | [`*models.Size8Enum`](../../doc/models/size-8-enum.md) | Query, Optional | Image size<br><br>**Default**: `"huge"` |
| `searchId` | `*string` | Query, Optional | Search ID that was provided in the results of an image search |

## Requires scope

### customer_accessCode

`licenses.create`, `purchases.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.LicenseImageResultDataList](../../doc/models/license-image-result-data-list.md).

## Example Usage

```go
ctx := context.Background()

body := models.LicenseImageRequest{
    Images:               []models.LicenseImageRequestImages{
        models.LicenseImageRequestImagesContainer.FromLicenseImage(models.LicenseImage{
            EditorialAcknowledgement: models.ToPointer(true),
            Format:                   models.ToPointer(models.FormatEnum_JPG),
            ImageId:                  "123456789",
            Metadata:                 models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
            Price:                    models.ToPointer(float64(12.34)),
            ShowModal:                models.ToPointer(true),
            Size:                     models.ToPointer(models.Size2Enum_SMALL),
            SubscriptionId:           models.ToPointer("s12345678"),
        }),
    },
}

size := models.Size8Enum_HUGE

apiResponse, err := imagesController.LicenseImages(ctx, body, nil, nil, &size, nil)
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


# Download Image

This endpoint redownloads images that you have already received a license for. The download links in the response are valid for 8 hours.

```go
DownloadImage(
    ctx context.Context,
    id string,
    body models.RedownloadImage) (
    models.ApiResponse[models.Url],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | License ID |
| `body` | [`models.RedownloadImage`](../../doc/models/redownload-image.md) | Body, Required | Information about the images to redownload |

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

body := models.RedownloadImage{
}

apiResponse, err := imagesController.DownloadImage(ctx, id, body)
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


# Get Image Recommendations

This endpoint returns images that customers put in the same collection as the specified image IDs.

```go
GetImageRecommendations(
    ctx context.Context,
    id []string,
    maxItems *int,
    safe *bool) (
    models.ApiResponse[models.RecommendationDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Required | Image IDs |
| `maxItems` | `*int` | Query, Optional | Maximum number of results returned in the response<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 500` |
| `safe` | `*bool` | Query, Optional | Restrict results to safe images<br><br>**Default**: `true` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.RecommendationDataList](../../doc/models/recommendation-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := []string{
    "id0",
}

maxItems := 20

safe := true

apiResponse, err := imagesController.GetImageRecommendations(ctx, id, &maxItems, &safe)
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


# Search Images

This endpoint searches for images. If you specify more than one search parameter, the API uses an AND condition. Array parameters can be specified multiple times; in this case, the API uses an AND or an OR condition with those values, depending on the parameter. You can also filter search terms out in the `query` parameter by prefixing the term with NOT. Free API accounts show results only from a limited library of media, not the full Shutterstock media library. Also, the number of search fields they can use in a request is limited.

```go
SearchImages(
    ctx context.Context,
    addedDate *time.Time,
    addedDateStart *time.Time,
    aspectRatioMin *float64,
    aspectRatioMax *float64,
    aspectRatio *float64,
    aiSearch *bool,
    aiLabelsLimit *int,
    aiIndustry *models.AiIndustryEnum,
    aiObjective *models.AiObjectiveEnum,
    addedDateEnd *time.Time,
    category *string,
    color *string,
    contributor []string,
    contributorCountry *models.SearchImagesContributorCountry,
    fields *string,
    height *int,
    heightFrom *int,
    heightTo *int,
    imageType []models.ImageType1Enum,
    keywordSafeSearch *bool,
    language *models.LanguageEnum,
    license []models.LicenseEnum,
    model []string,
    orientation *models.Orientation1Enum,
    page *int,
    perPage *int,
    peopleModelReleased *bool,
    peopleAge *models.PeopleAge1Enum,
    peopleEthnicity []models.PeopleEthnicity1Enum,
    peopleGender *models.PeopleGender1Enum,
    peopleNumber *int,
    query *string,
    region *models.SearchImagesRegion,
    safe *bool,
    sort *models.Sort4Enum,
    spellcheckQuery *bool,
    view *models.View1Enum,
    width *int,
    widthFrom *int,
    widthTo *int) (
    models.ApiResponse[models.ImageSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `addedDate` | `*time.Time` | Query, Optional | Show images added on the specified date |
| `addedDateStart` | `*time.Time` | Query, Optional | Show images added on or after the specified date |
| `aspectRatioMin` | `*float64` | Query, Optional | Show images with the specified aspect ratio or higher, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `> 0` |
| `aspectRatioMax` | `*float64` | Query, Optional | Show images with the specified aspect ratio or lower, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `> 0` |
| `aspectRatio` | `*float64` | Query, Optional | Show images with the specified aspect ratio, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `> 0` |
| `aiSearch` | `*bool` | Query, Optional | Set to true and specify the `ai_objective` and `ai_industry` parameters to use AI-powered search; the API returns information about how well images meet the objective for the industry |
| `aiLabelsLimit` | `*int` | Query, Optional | For AI-powered search, specify the maximum number of labels to return<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 500` |
| `aiIndustry` | [`*models.AiIndustryEnum`](../../doc/models/ai-industry-enum.md) | Query, Optional | For AI-powered search, specify the industry to target; requires that the `ai_search` parameter is set to true |
| `aiObjective` | [`*models.AiObjectiveEnum`](../../doc/models/ai-objective-enum.md) | Query, Optional | For AI-powered search, specify the goal of the media; requires that the `ai_search` parameter is set to true |
| `addedDateEnd` | `*time.Time` | Query, Optional | Show images added before the specified date |
| `category` | `*string` | Query, Optional | Show images with the specified Shutterstock-defined category; specify a category name or ID |
| `color` | `*string` | Query, Optional | Specify either a hexadecimal color in the format '4F21EA' or 'grayscale'; the API returns images that use similar colors |
| `contributor` | `[]string` | Query, Optional | Show images with the specified contributor names or IDs, allows multiple |
| `contributorCountry` | [`*models.SearchImagesContributorCountry`](../../doc/models/containers/search-images-contributor-country.md) | Query, Optional | This is a container for one-of cases. |
| `fields` | `*string` | Query, Optional | Fields to display in the response; see the documentation for the fields parameter in the overview section |
| `height` | `*int` | Query, Optional | (Deprecated; use height_from and height_to instead) Show images with the specified height |
| `heightFrom` | `*int` | Query, Optional | Show images with the specified height or larger, in pixels |
| `heightTo` | `*int` | Query, Optional | Show images with the specified height or smaller, in pixels |
| `imageType` | [`[]models.ImageType1Enum`](../../doc/models/image-type-1-enum.md) | Query, Optional | Show images of the specified type |
| `keywordSafeSearch` | `*bool` | Query, Optional | Hide results with potentially unsafe keywords<br><br>**Default**: `true` |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Set query and result language (uses Accept-Language header if not set) |
| `license` | [`[]models.LicenseEnum`](../../doc/models/license-enum.md) | Query, Optional | Show only images with the specified license |
| `model` | `[]string` | Query, Optional | Show image results with the specified model IDs |
| `orientation` | [`*models.Orientation1Enum`](../../doc/models/orientation-1-enum.md) | Query, Optional | Show image results with horizontal or vertical orientation |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 500` |
| `peopleModelReleased` | `*bool` | Query, Optional | Show images of people with a signed model release |
| `peopleAge` | [`*models.PeopleAge1Enum`](../../doc/models/people-age-1-enum.md) | Query, Optional | Show images that feature people of the specified age category |
| `peopleEthnicity` | [`[]models.PeopleEthnicity1Enum`](../../doc/models/people-ethnicity-1-enum.md) | Query, Optional | Show images with people of the specified ethnicities, or start with NOT to show images without those ethnicities |
| `peopleGender` | [`*models.PeopleGender1Enum`](../../doc/models/people-gender-1-enum.md) | Query, Optional | Show images with people of the specified gender |
| `peopleNumber` | `*int` | Query, Optional | Show images with the specified number of people<br><br>**Constraints**: `>= 0`, `<= 4` |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces; you can use NOT to filter out images that match a term |
| `region` | [`*models.SearchImagesRegion`](../../doc/models/containers/search-images-region.md) | Query, Optional | This is a container for any-of cases. |
| `safe` | `*bool` | Query, Optional | Enable or disable safe search<br><br>**Default**: `true` |
| `sort` | [`*models.Sort4Enum`](../../doc/models/sort-4-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"popular"` |
| `spellcheckQuery` | `*bool` | Query, Optional | Spellcheck the search query and return results on suggested spellings<br><br>**Default**: `true` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `width` | `*int` | Query, Optional | (Deprecated; use width_from and width_to instead) Show images with the specified width |
| `widthFrom` | `*int` | Query, Optional | Show images with the specified width or larger, in pixels |
| `widthTo` | `*int` | Query, Optional | Show images with the specified width or smaller, in pixels |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.ImageSearchResults](../../doc/models/image-search-results.md).

## Example Usage

```go
ctx := context.Background()

addedDate := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

addedDateStart := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

aspectRatioMin := float64(1.7778)

aspectRatioMax := float64(1.7778)

aspectRatio := float64(1.7778)

aiLabelsLimit := 20

addedDateEnd := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

color := "4F21EA"

contributor := []string{
    "123456",
}

heightFrom := 1080

heightTo := 1080

keywordSafeSearch := true

language := models.LanguageEnum_FR

model := []string{
    "12345",
    "67890",
}

orientation := models.Orientation1Enum_VERTICAL

page := 1

perPage := 50

peopleModelReleased := true

peopleAge := models.PeopleAge1Enum_ENUM20S

peopleGender := models.PeopleGender1Enum_BOTH

peopleNumber := 2

query := "dogs on the beach"

region := models.SearchImagesRegionContainer.FromString("US")

safe := true

sort := models.Sort4Enum_POPULAR

spellcheckQuery := true

view := models.View1Enum_MINIMAL

widthFrom := 1920

widthTo := 1920

apiResponse, err := imagesController.SearchImages(ctx, &addedDate, &addedDateStart, &aspectRatioMin, &aspectRatioMax, &aspectRatio, nil, &aiLabelsLimit, nil, nil, &addedDateEnd, nil, &color, contributor, nil, nil, nil, &heightFrom, &heightTo, nil, &keywordSafeSearch, &language, nil, model, &orientation, &page, &perPage, &peopleModelReleased, &peopleAge, nil, &peopleGender, &peopleNumber, &query, &region, &safe, &sort, &spellcheckQuery, &view, nil, &widthFrom, &widthTo)
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


# Get Image Suggestions

This endpoint provides autocomplete suggestions for partial search terms.

```go
GetImageSuggestions(
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
| `limit` | `*int` | Query, Optional | Limit the number of suggestions<br><br>**Default**: `10`<br><br>**Constraints**: `>= 1`, `<= 25` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Suggestions](../../doc/models/suggestions.md).

## Example Usage

```go
ctx := context.Background()

query := "cats"

limit := 10

apiResponse, err := imagesController.GetImageSuggestions(ctx, query, &limit)
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


# Get Image Keyword Suggestions

This endpoint returns up to 10 important keywords from a block of plain text.

```go
GetImageKeywordSuggestions(
    ctx context.Context,
    body models.SearchEntitiesRequest) (
    models.ApiResponse[models.SearchEntitiesResponse],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.SearchEntitiesRequest`](../../doc/models/search-entities-request.md) | Body, Required | Plain text to extract keywords from |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.SearchEntitiesResponse](../../doc/models/search-entities-response.md).

## Example Usage

```go
ctx := context.Background()

body := models.SearchEntitiesRequest{
    Text:                 "Planting flowers is a great way to make springtime more beautiful.",
}

apiResponse, err := imagesController.GetImageKeywordSuggestions(ctx, body)
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
    "beach",
    "place",
    "sand",
    "ocean"
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# Get Updated Images

This endpoint lists images that have been updated in the specified time period to update content management systems (CMS) or digital asset management (DAM) systems. In most cases, use the `interval` parameter to show images that were updated recently, but you can also use the `start_date` and `end_date` parameters to specify a range of no more than three days. Do not use the `interval` parameter with either `start_date` or `end_date`.

```go
GetUpdatedImages(
    ctx context.Context,
    mType []models.Type5Enum,
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
| `mType` | [`[]models.Type5Enum`](../../doc/models/type-5-enum.md) | Query, Optional | Show images that were added, deleted, or edited; by default, the endpoint returns images that were updated in any of these ways |
| `startDate` | `*time.Time` | Query, Optional | Show images updated on or after the specified date |
| `endDate` | `*time.Time` | Query, Optional | Show images updated before the specified date |
| `interval` | `*string` | Query, Optional | Show images updated in the specified time period, where the time period is an interval (like SQL INTERVAL) such as 1 DAY, 6 HOUR, or 30 MINUTE; the default is 1 HOUR, which shows images that were updated in the hour preceding the request<br><br>**Default**: `"1 HOUR"` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `100`<br><br>**Constraints**: `>= 1`, `<= 2000` |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort order<br><br>**Default**: `"newest"` |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.UpdatedMediaDataList](../../doc/models/updated-media-data-list.md).

## Example Usage

```go
ctx := context.Background()

startDate := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

interval := "1 HOUR"

page := 1

perPage := 100

sort := models.Sort1Enum_NEWEST

apiResponse, err := imagesController.GetUpdatedImages(ctx, nil, &startDate, &endDate, &interval, &page, &perPage, &sort)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Get Image

This endpoint shows information about an image, including a URL to a preview image and the sizes that it is available in.

```go
GetImage(
    ctx context.Context,
    id string,
    language *models.LanguageEnum,
    view *models.View1Enum,
    searchId *string) (
    models.ApiResponse[models.Image],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | Image ID |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Language for the keywords and categories in the response |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"full"` |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Image](../../doc/models/image.md).

## Example Usage

```go
ctx := context.Background()

id := "465011609"

language := models.LanguageEnum_ES

view := models.View1Enum_FULL

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := imagesController.GetImage(ctx, id, &language, &view, &searchId)
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


# List Similar Images

This endpoint returns images that are visually similar to an image that you specify.

```go
ListSimilarImages(
    ctx context.Context,
    id string,
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
| `id` | `string` | Template, Required | Image ID<br><br>**Constraints**: *Pattern*: `^([1-9]\d*)\|(U[a-zA-Z0-9]+)$` |
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

id := "465011609"

language := models.LanguageEnum_ES

page := 1

perPage := 20

view := models.View1Enum_MINIMAL

apiResponse, err := imagesController.ListSimilarImages(ctx, id, &language, &page, &perPage, &view)
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

