# Contributors

```go
contributorsController := client.ContributorsController()
```

## Class Name

`ContributorsController`

## Methods

* [Get Contributor List](../../doc/controllers/contributors.md#get-contributor-list)
* [Get Contributor](../../doc/controllers/contributors.md#get-contributor)
* [Get Contributor Collections List](../../doc/controllers/contributors.md#get-contributor-collections-list)
* [Get Contributor Collections](../../doc/controllers/contributors.md#get-contributor-collections)
* [Get Contributor Collection Items](../../doc/controllers/contributors.md#get-contributor-collection-items)


# Get Contributor List

This endpoint lists information about one or more contributors, including contributor type, equipment they use and other attributes.

```go
GetContributorList(
    ctx context.Context,
    id []string) (
    models.ApiResponse[models.ContributorProfileDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md) **OR** [basic](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Required | One or more contributor IDs |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.ContributorProfileDataList](../../doc/models/contributor-profile-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := []string{
    "id0",
    "id1",
}

apiResponse, err := contributorsController.GetContributorList(ctx, id)
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


# Get Contributor

This endpoint shows information about a single contributor, including contributor type, equipment they use, and other attributes.

```go
GetContributor(
    ctx context.Context,
    contributorId string) (
    models.ApiResponse[models.ContributorProfile],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md) **OR** [basic](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `contributorId` | `string` | Template, Required | Contributor ID |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.ContributorProfile](../../doc/models/contributor-profile.md).

## Example Usage

```go
ctx := context.Background()

contributorId := "1653538"

apiResponse, err := contributorsController.GetContributor(ctx, contributorId)
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


# Get Contributor Collections List

This endpoint lists collections based on contributor ID.

```go
GetContributorCollectionsList(
    ctx context.Context,
    contributorId string,
    sort *models.Sort7Enum) (
    models.ApiResponse[models.CollectionDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md) **OR** [basic](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `contributorId` | `string` | Template, Required | Contributor ID |
| `sort` | [`*models.Sort7Enum`](../../doc/models/sort-7-enum.md) | Query, Optional | Sort order |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionDataList](../../doc/models/collection-data-list.md).

## Example Usage

```go
ctx := context.Background()

contributorId := "800506"

apiResponse, err := contributorsController.GetContributorCollectionsList(ctx, contributorId, nil)
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
| 404 | Contributor not found | `ApiError` |


# Get Contributor Collections

This endpoint gets more detailed information about a contributor's collection, including its cover image, timestamps for its creation, and most recent update. To get the items in collections, use GET /v2/contributors/{contributor_id}/collections/{id}/items.

```go
GetContributorCollections(
    ctx context.Context,
    contributorId string,
    id string) (
    models.ApiResponse[models.Collection],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md) **OR** [basic](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `contributorId` | `string` | Template, Required | Contributor ID |
| `id` | `string` | Template, Required | Collection ID that belongs to the contributor |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Collection](../../doc/models/collection.md).

## Example Usage

```go
ctx := context.Background()

contributorId := "800506"

id := "1991678"

apiResponse, err := contributorsController.GetContributorCollections(ctx, contributorId, id)
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
| 404 | Set not found | `ApiError` |


# Get Contributor Collection Items

This endpoint lists the IDs of items in a contributor's collection and the date that each was added.

```go
GetContributorCollectionItems(
    ctx context.Context,
    contributorId string,
    id string,
    page *int,
    perPage *int,
    sort *models.Sort1Enum) (
    models.ApiResponse[models.CollectionItemDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md) **OR** [basic](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `contributorId` | `string` | Template, Required | Contributor ID |
| `id` | `string` | Template, Required | Collection ID that belongs to the contributor |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort order |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionItemDataList](../../doc/models/collection-item-data-list.md).

## Example Usage

```go
ctx := context.Background()

contributorId := "800506"

id := "1991678"

page := 1

perPage := 20

apiResponse, err := contributorsController.GetContributorCollectionItems(ctx, contributorId, id, &page, &perPage, nil)
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
      "added_time": "2014-05-01T05:49:46-04:00",
      "id": "168592952",
      "media_type": "image"
    },
    {
      "added_time": "2014-05-01T05:49:59-04:00",
      "id": "88269310",
      "media_type": "image"
    },
    {
      "added_time": "2014-05-01T05:50:21-04:00",
      "id": "94373977",
      "media_type": "image"
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
| 404 | Set not found | `ApiError` |

