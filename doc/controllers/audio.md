# Audio

```go
audioController := client.AudioController()
```

## Class Name

`AudioController`

## Methods

* [Get Track List](../../doc/controllers/audio.md#get-track-list)
* [Get Track Collection List](../../doc/controllers/audio.md#get-track-collection-list)
* [Create Track Collection](../../doc/controllers/audio.md#create-track-collection)
* [Delete Track Collection](../../doc/controllers/audio.md#delete-track-collection)
* [Get Track Collection](../../doc/controllers/audio.md#get-track-collection)
* [Rename Track Collection](../../doc/controllers/audio.md#rename-track-collection)
* [Delete Track Collection Items](../../doc/controllers/audio.md#delete-track-collection-items)
* [Get Track Collection Items](../../doc/controllers/audio.md#get-track-collection-items)
* [Add Track Collection Items](../../doc/controllers/audio.md#add-track-collection-items)
* [List Genres](../../doc/controllers/audio.md#list-genres)
* [List Instruments](../../doc/controllers/audio.md#list-instruments)
* [Get Track License List](../../doc/controllers/audio.md#get-track-license-list)
* [License Track](../../doc/controllers/audio.md#license-track)
* [Download Tracks](../../doc/controllers/audio.md#download-tracks)
* [List Moods](../../doc/controllers/audio.md#list-moods)
* [Search Tracks](../../doc/controllers/audio.md#search-tracks)
* [Get Track](../../doc/controllers/audio.md#get-track)


# Get Track List

This endpoint lists information about one or more audio tracks, including the description and publication date.

```go
GetTrackList(
    ctx context.Context,
    id []string,
    view *models.View1Enum,
    searchId *string) (
    models.ApiResponse[models.AudioDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Required | One or more audio IDs<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `500`, *Pattern*: `^[1-9]\d*$` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.AudioDataList](../../doc/models/audio-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := []string{
    "442583",
    "434750",
}

view := models.View1Enum_FULL

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := audioController.GetTrackList(ctx, id, &view, &searchId)
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


# Get Track Collection List

This endpoint lists your collections of audio tracks and their basic attributes.

```go
GetTrackCollectionList(
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

apiResponse, err := audioController.GetTrackCollectionList(ctx, &page, &perPage, nil)
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


# Create Track Collection

This endpoint creates one or more collections (soundboxes). To add tracks, use `POST /v2/audio/collections/{id}/items`.

```go
CreateTrackCollection(
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

**201**: Successfully created audio collection

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.CollectionCreateResponse](../../doc/models/collection-create-response.md).

## Example Usage

```go
ctx := context.Background()

body := models.CollectionCreateRequest{
    Name:                 "Best rock music",
}

apiResponse, err := audioController.CreateTrackCollection(ctx, body)
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


# Delete Track Collection

This endpoint deletes a collection.

```go
DeleteTrackCollection(
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

id := "48433111"

resp, err := audioController.DeleteTrackCollection(ctx, id)
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


# Get Track Collection

This endpoint gets more detailed information about a collection, including the number of items in it and when it was last updated. To get the tracks in collections, use `GET /v2/audio/collections/{id}/items`.

```go
GetTrackCollection(
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

id := "48433107"

apiResponse, err := audioController.GetTrackCollection(ctx, id, nil, nil)
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


# Rename Track Collection

This endpoint sets a new name for a collection.

```go
RenameTrackCollection(
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
| `body` | [`models.CollectionUpdateRequest`](../../doc/models/collection-update-request.md) | Body, Required | Collection changes |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully updated collection

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "48433107"

body := models.CollectionUpdateRequest{
    Name:                 "Best rock music",
}

resp, err := audioController.RenameTrackCollection(ctx, id, body)
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


# Delete Track Collection Items

This endpoint removes one or more tracks from a collection.

```go
DeleteTrackCollectionItems(
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
| `itemId` | `[]string` | Query, Optional | One or more item IDs to remove from the collection |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully removed collection items

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "48433119"

itemId := []string{
    "76688182",
    "40005859",
}

resp, err := audioController.DeleteTrackCollectionItems(ctx, id, itemId)
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


# Get Track Collection Items

This endpoint lists the IDs of tracks in a collection and the date that each was added.

```go
GetTrackCollectionItems(
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

apiResponse, err := audioController.GetTrackCollectionItems(ctx, id, &page, &perPage, nil, &sort)
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
      "added_time": "2016-08-18T18:52:59-04:00",
      "id": "76688182",
      "media_type": "audio"
    },
    {
      "added_time": "2016-08-18T18:52:59-04:00",
      "id": "40005859",
      "media_type": "audio"
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
| 404 | Collection not found | `ApiError` |


# Add Track Collection Items

This endpoint adds one or more tracks to a collection by track IDs.

```go
AddTrackCollectionItems(
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
| `body` | [`models.CollectionItemRequest`](../../doc/models/collection-item-request.md) | Body, Required | List of items to add to collection |

## Requires scope

### customer_accessCode

`collections.edit`

## Response Type

**204**: Successfully added collection items

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```go
ctx := context.Background()

id := "48433115"

body := models.CollectionItemRequest{
    Items:                []models.CollectionItem{
        models.CollectionItem{
            Id:                   "442583",
        },
        models.CollectionItem{
            Id:                   "7491192",
        },
    },
}

resp, err := audioController.AddTrackCollectionItems(ctx, id, body)
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


# List Genres

This endpoint returns a list of all audio genres.

```go
ListGenres(
    ctx context.Context,
    language *string) (
    models.ApiResponse[models.GenreList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `language` | `*string` | Query, Optional | Which language the genres will be returned |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.GenreList](../../doc/models/genre-list.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := audioController.ListGenres(ctx, nil)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# List Instruments

This endpoint returns a list of all audio instruments.

```go
ListInstruments(
    ctx context.Context,
    language *string) (
    models.ApiResponse[models.InstrumentList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `language` | `*string` | Query, Optional | Which language the instruments will be returned in |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.InstrumentList](../../doc/models/instrument-list.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := audioController.ListInstruments(ctx, nil)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Get Track License List

This endpoint lists existing licenses. You can filter the results according to the track ID to see if you have an existing license for a specific track.

```go
GetTrackLicenseList(
    ctx context.Context,
    audioId *string,
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
| `audioId` | `*string` | Query, Optional | Show licenses for the specified track ID |
| `license` | `*string` | Query, Optional | Restrict results by license. Prepending a `-` sign will exclude results by license |
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

audioId := "1"

license := "48433107"

page := 1

perPage := 20

sort := models.Sort1Enum_NEWEST

username := "aUniqueUsername"

startDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

downloadAvailability := models.DownloadAvailabilityEnum_ALL

teamHistory := false

apiResponse, err := audioController.GetTrackLicenseList(ctx, &audioId, &license, &page, &perPage, &sort, &username, &startDate, &endDate, &downloadAvailability, &teamHistory)
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
      "audio": {
        "format": {
          "size": "clean_audio"
        },
        "id": "420298"
      },
      "download_time": "2020-11-11T16:15:20.000Z",
      "id": "a10b7a7a5a02113a928f13e5ba196151d6",
      "is_downloadable": true,
      "license": "premier_music_extended",
      "metadata": {
        "purchase_order": "123"
      },
      "user": {
        "username": "jsmith"
      }
    }
  ],
  "page": 1,
  "per_page": 20,
  "total_count": 1
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# License Track

This endpoint gets licenses for one or more tracks. The download links in the response are valid for 8 hours.

```go
LicenseTrack(
    ctx context.Context,
    body models.LicenseAudioRequest,
    license *models.License3Enum,
    searchId *string) (
    models.ApiResponse[models.LicenseAudioResultDataList],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.LicenseAudioRequest`](../../doc/models/license-audio-request.md) | Body, Required | Tracks to license |
| `license` | [`*models.License3Enum`](../../doc/models/license-3-enum.md) | Query, Optional | License type |
| `searchId` | `*string` | Query, Optional | The ID of the search that led to licensing this track |

## Requires scope

### customer_accessCode

`licenses.create`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.LicenseAudioResultDataList](../../doc/models/license-audio-result-data-list.md).

## Example Usage

```go
ctx := context.Background()

body := models.LicenseAudioRequest{
    Audio:                []models.LicenseAudio{
        models.LicenseAudio{
            AudioId:              "591623",
            License:              models.ToPointer(models.License1Enum_AUDIOPLATFORM),
        },
    },
}

license := models.License3Enum_AUDIOPLATFORM

searchId := "p5S6QwRikdFJTHXwsoiqTg"

apiResponse, err := audioController.LicenseTrack(ctx, body, &license, &searchId)
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


# Download Tracks

This endpoint redownloads tracks that you have already received a license for. The download links in the response are valid for 8 hours.

```go
DownloadTracks(
    ctx context.Context,
    id string) (
    models.ApiResponse[models.AudioUrl],
    error)
```

## Authentication

This endpoint requires [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | License ID |

## Requires scope

### customer_accessCode

`licenses.view`

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.AudioUrl](../../doc/models/audio-url.md).

## Example Usage

```go
ctx := context.Background()

id := "e123"

apiResponse, err := audioController.DownloadTracks(ctx, id)
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
  "shorts_loops_stems": "http://download2.dev.shutterstock.com/gatekeeper/abc/original.zip",
  "url": "http://download2.dev.shutterstock.com/gatekeeper/abc/original.wav"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# List Moods

This endpoint returns a list of all audio moods.

```go
ListMoods(
    ctx context.Context,
    language *string) (
    models.ApiResponse[models.MoodList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `language` | `*string` | Query, Optional | Which language the moods will be returned in |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.MoodList](../../doc/models/mood-list.md).

## Example Usage

```go
ctx := context.Background()

apiResponse, err := audioController.ListMoods(ctx, nil)
if err != nil {
    log.Fatalln(err)
} else {
    // Printing the result and response
    fmt.Println(apiResponse.Data)
    fmt.Println(apiResponse.Response.StatusCode)
}
```


# Search Tracks

This endpoint searches for tracks. If you specify more than one search parameter, the API uses an AND condition. Array parameters can be specified multiple times; in this case, the API uses an AND or an OR condition with those values, depending on the parameter.

```go
SearchTracks(
    ctx context.Context,
    artists []string,
    bpm *int,
    bpmFrom *int,
    bpmTo *int,
    duration *int,
    durationFrom *int,
    durationTo *int,
    genre []string,
    isInstrumental *bool,
    instruments []string,
    moods []string,
    page *int,
    perPage *int,
    query *string,
    sort *models.Sort3Enum,
    sortOrder *models.SortOrderEnum,
    vocalDescription *string,
    view *models.View1Enum,
    fields *string,
    library *models.LibraryEnum,
    language *string) (
    models.ApiResponse[models.AudioSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `artists` | `[]string` | Query, Optional | Show tracks with one of the specified artist names or IDs |
| `bpm` | `*int` | Query, Optional | (Deprecated; use bpm_from and bpm_to instead) Show tracks with the specified beats per minute |
| `bpmFrom` | `*int` | Query, Optional | Show tracks with the specified beats per minute or faster |
| `bpmTo` | `*int` | Query, Optional | Show tracks with the specified beats per minute or slower |
| `duration` | `*int` | Query, Optional | Show tracks with the specified duration in seconds |
| `durationFrom` | `*int` | Query, Optional | Show tracks with the specified duration or longer in seconds |
| `durationTo` | `*int` | Query, Optional | Show tracks with the specified duration or shorter in seconds |
| `genre` | `[]string` | Query, Optional | Show tracks with each of the specified genres; to get the list of genres, use `GET /v2/audio/genres` |
| `isInstrumental` | `*bool` | Query, Optional | Show instrumental music only |
| `instruments` | `[]string` | Query, Optional | Show tracks with each of the specified instruments; to get the list of instruments, use `GET /v2/audio/instruments` |
| `moods` | `[]string` | Query, Optional | Show tracks with each of the specified moods; to get the list of moods, use `GET /v2/audio/moods` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 500` |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces |
| `sort` | [`*models.Sort3Enum`](../../doc/models/sort-3-enum.md) | Query, Optional | Sort by |
| `sortOrder` | [`*models.SortOrderEnum`](../../doc/models/sort-order-enum.md) | Query, Optional | Sort order<br><br>**Default**: `"desc"` |
| `vocalDescription` | `*string` | Query, Optional | Show tracks with the specified vocal description (male, female) |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `fields` | `*string` | Query, Optional | Fields to display in the response; see the documentation for the fields parameter in the overview section |
| `library` | [`*models.LibraryEnum`](../../doc/models/library-enum.md) | Query, Optional | Which library to search<br><br>**Default**: `"premier"` |
| `language` | `*string` | Query, Optional | Which language to search in |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.AudioSearchResults](../../doc/models/audio-search-results.md).

## Example Usage

```go
ctx := context.Background()

bpmFrom := 80

bpmTo := 120

duration := 180

durationFrom := 30

durationTo := 180

genre := []string{
    "Classical",
    "Holiday",
}

isInstrumental := true

instruments := []string{
    "Trumpet",
    "Percussion",
}

moods := []string{
    "Confident",
    "Playful",
}

page := 1

perPage := 1

query := "drum"

sort := models.Sort3Enum_SCORE

sortOrder := models.SortOrderEnum_DESC

vocalDescription := "female"

view := models.View1Enum_FULL

library := models.LibraryEnum_PREMIER

apiResponse, err := audioController.SearchTracks(ctx, nil, nil, &bpmFrom, &bpmTo, &duration, &durationFrom, &durationTo, genre, &isInstrumental, instruments, moods, &page, &perPage, &query, &sort, &sortOrder, &vocalDescription, &view, nil, &library, nil)
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


# Get Track

This endpoint shows information about a track, including its genres, instruments, and other attributes.

```go
GetTrack(
    ctx context.Context,
    id int,
    view *models.View1Enum,
    searchId *string) (
    models.ApiResponse[models.Audio],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `int` | Template, Required | Audio track ID |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"full"` |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.Audio](../../doc/models/audio.md).

## Example Usage

```go
ctx := context.Background()

id := 442583

view := models.View1Enum_FULL

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := audioController.GetTrack(ctx, id, &view, &searchId)
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

