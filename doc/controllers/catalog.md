# Catalog

```go
catalogController := client.CatalogController()
```

## Class Name

`CatalogController`

## Methods

* [Get Collections](../../doc/controllers/catalog.md#get-collections)
* [Create Collection](../../doc/controllers/catalog.md#create-collection)
* [Delete Collection](../../doc/controllers/catalog.md#delete-collection)
* [Update Collection](../../doc/controllers/catalog.md#update-collection)
* [Delete from Collection](../../doc/controllers/catalog.md#delete-from-collection)
* [Add to Collection](../../doc/controllers/catalog.md#add-to-collection)
* [Search Catalog](../../doc/controllers/catalog.md#search-catalog)


# Get Collections

This endpoint returns a list of catalog collections.

```go
GetCollections(
    ctx context.Context,
    page *int,
    perPage *int,
    sort *models.Sort1Enum,
    shared *bool) (
    models.ApiResponse[models.CatalogCollectionDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 2`, `<= 50` |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"newest"` |
| `shared` | `*bool` | Query, Optional | Set to true to omit collections that you own and return only collections  that are shared with you<br><br>**Default**: `false` |

## Requires scope

### customer_accessCode

`collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CatalogCollectionDataList](../../doc/models/catalog-collection-data-list.md).

## Example Usage

```go
ctx := context.Background()

page := 1

perPage := 20

sort := models.Sort1Enum_NEWEST

shared := false

apiResponse, err := catalogController.GetCollections(ctx, &page, &perPage, &sort, &shared)
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
| 400 | Invalid status value | `ApiError` |


# Create Collection

This endpoint creates a catalog collection and optionally adds assets. To add assets to the collection later, use `PATCH /v2/catalog/collections/{collection_id}/items`.

```go
CreateCollection(
    ctx context.Context,
    body models.CreateCatalogCollection) (
    models.ApiResponse[models.CatalogCollection],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.CreateCatalogCollection`](../../doc/models/create-catalog-collection.md) | Body, Required | Create a catalog collection and, optionally, add items. |

## Requires scope

### customer_accessCode

`collections.edit`, `collections.view`

## Response Type

**201**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CatalogCollection](../../doc/models/catalog-collection.md).

## Example Usage

```go
ctx := context.Background()

body := models.CreateCatalogCollection{
    Items:                []models.CreateCatalogCollectionItem{
        models.CreateCatalogCollectionItem{
            Asset:                models.Asset1{
                Id:                   models.ToPointer("1690105108"),
                Type:                 "image",
            },
        },
    },
    Name:                 "New Collection",
    Visibility:           models.ToPointer(models.VisibilityEnum_PUBLIC),
}

apiResponse, err := catalogController.CreateCollection(ctx, body)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Delete Collection

This endpoint deletes a catalog collection. It does not remove the assets from the user's account's catalog.

```go
DeleteCollection(
    ctx context.Context,
    collectionId string) (
    http.Response,
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `collectionId` | `string` | Template, Required | The ID of the collection to delete |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

collectionId := "126351028"

resp, err := catalogController.DeleteCollection(ctx, collectionId)
if err != nil {
    log.Fatalln(err)
} else {
    fmt.Println(resp.StatusCode)
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Collection not found | `ApiError` |


# Update Collection

This endpoint updates the metadata of a catalog collection.

```go
UpdateCollection(
    ctx context.Context,
    collectionId string,
    body models.UpdateCatalogCollection) (
    models.ApiResponse[models.CatalogCollection],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `collectionId` | `string` | Template, Required | ID of collection that needs to be modified |
| `body` | [`models.UpdateCatalogCollection`](../../doc/models/update-catalog-collection.md) | Body, Required | Collections Metadata to update |

## Requires scope

### customer_accessCode

`collections.edit`, `collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CatalogCollection](../../doc/models/catalog-collection.md).

## Example Usage

```go
ctx := context.Background()

collectionId := "126351028"

body := models.UpdateCatalogCollection{
}

apiResponse, err := catalogController.UpdateCollection(ctx, collectionId, body)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Delete from Collection

This endpoint removes assets from a catalog collection. It does not remove the assets from the user's account's catalog.

```go
DeleteFromCollection(
    ctx context.Context,
    collectionId string,
    body models.RemoveCatalogCollectionItems) (
    models.ApiResponse[models.CatalogCollection],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `collectionId` | `string` | Template, Required | The ID of the collection to remove assets from |
| `body` | [`models.RemoveCatalogCollectionItems`](../../doc/models/remove-catalog-collection-items.md) | Body, Required | Items to remove from the collection |

## Requires scope

### customer_accessCode

`collections.edit`, `collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CatalogCollection](../../doc/models/catalog-collection.md).

## Example Usage

```go
ctx := context.Background()

collectionId := "126351028"

body := models.RemoveCatalogCollectionItems{
    Items:                []models.RemoveCatalogCollectionItem{
        models.RemoveCatalogCollectionItem{
            Id:                   "123",
        },
    },
}

apiResponse, err := catalogController.DeleteFromCollection(ctx, collectionId, body)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Add to Collection

This endpoint adds assets to a catalog collection. It also automatically adds the assets to the user's account's catalog.

```go
AddToCollection(
    ctx context.Context,
    collectionId string,
    body models.CreateCatalogCollectionItems) (
    models.ApiResponse[models.CatalogCollection],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `collectionId` | `string` | Template, Required | The ID of the collection to add assets to |
| `body` | [`models.CreateCatalogCollectionItems`](../../doc/models/create-catalog-collection-items.md) | Body, Required | Collection item attributes to add to collection |

## Requires scope

### customer_accessCode

`collections.edit`, `collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CatalogCollection](../../doc/models/catalog-collection.md).

## Example Usage

```go
ctx := context.Background()

collectionId := "126351028"

body := models.CreateCatalogCollectionItems{
    Items:                []models.CreateCatalogCollectionItem{
        models.CreateCatalogCollectionItem{
            Asset:                models.Asset1{
                Id:                   models.ToPointer("1690105108"),
                Type:                 "image",
            },
        },
    },
}

apiResponse, err := catalogController.AddToCollection(ctx, collectionId, body)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Search Catalog

This endpoint searches for assets in the account's catalog. If you specify more than one search parameter, the API uses an AND condition. Array parameters can be specified multiple times; in this case, the API uses an AND or an OR condition with those values, depending on the parameter. You can also filter search terms out in the `query` parameter by prefixing the term with NOT.

```go
SearchCatalog(
    ctx context.Context,
    sort *models.Sort1Enum,
    page *int,
    perPage *int,
    query *string,
    collectionId []string,
    assetType []models.AssetTypeEnum) (
    models.ApiResponse[models.CatalogCollectionItemDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"newest"` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 500` |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces |
| `collectionId` | `[]string` | Query, Optional | Filter by collection id<br><br>**Constraints**: *Maximum Items*: `50` |
| `assetType` | [`[]models.AssetTypeEnum`](../../doc/models/asset-type-enum.md) | Query, Optional | Filter by asset type |

## Requires scope

### customer_accessCode

`collections.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CatalogCollectionItemDataList](../../doc/models/catalog-collection-item-data-list.md).

## Example Usage

```go
ctx := context.Background()

sort := models.Sort1Enum_NEWEST

page := 1

perPage := 50

query := "dogs on the beach"

collectionId := []string{
    "123456",
    "456789",
    "13579",
}

assetType := []models.AssetTypeEnum{
    models.AssetTypeEnum_IMAGE,
    models.AssetTypeEnum_EDITORIALIMAGE,
}

apiResponse, err := catalogController.SearchCatalog(ctx, &sort, &page, &perPage, &query, collectionId, assetType)
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

