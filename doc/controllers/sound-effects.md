# Sound Effects

```go
soundEffectsController := client.SoundEffectsController()
```

## Class Name

`SoundEffectsController`

## Methods

* [Get Sfx List Details](../../doc/controllers/sound-effects.md#get-sfx-list-details)
* [Get Sfx License List](../../doc/controllers/sound-effects.md#get-sfx-license-list)
* [Licenses SFX](../../doc/controllers/sound-effects.md#licenses-sfx)
* [Download Sfx](../../doc/controllers/sound-effects.md#download-sfx)
* [Search SFX](../../doc/controllers/sound-effects.md#search-sfx)
* [Get Sfx Details](../../doc/controllers/sound-effects.md#get-sfx-details)


# Get Sfx List Details

This endpoint shows information about sound effects.

```go
GetSfxListDetails(
    ctx context.Context,
    id []string,
    view *models.View1Enum,
    language *models.LanguageEnum,
    library *models.Library1Enum,
    searchId *string) (
    models.ApiResponse[models.SFXDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Required | One or more sound effect IDs<br><br>**Constraints**: *Maximum Items*: `500` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Language for the keywords and categories in the response |
| `library` | [`*models.Library1Enum`](../../doc/models/library-1-enum.md) | Query, Optional | Which library to fetch from |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.SFXDataList](../../doc/models/sfx-data-list.md).

## Example Usage

```go
ctx := context.Background()

id := []string{
    "1110335168",
    "465011609",
}

view := models.View1Enum_MINIMAL

language := models.LanguageEnum_CS

library := models.Library1Enum_SHUTTERSTOCK

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := soundEffectsController.GetSfxListDetails(ctx, id, &view, &language, &library, &searchId)
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


# Get Sfx License List

This endpoint lists existing licenses.

```go
GetSfxLicenseList(
    ctx context.Context,
    sfxId *string,
    license *string,
    page *int,
    perPage *int,
    sort *models.Sort1Enum,
    username *string,
    startDate *time.Time,
    endDate *time.Time,
    licenseId *string,
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
| `sfxId` | `*string` | Query, Optional | Show licenses for the specified sound effects ID<br><br>**Constraints**: *Pattern*: `^[1-9]\d*$` |
| `license` | `*string` | Query, Optional | Show sound effects that are available with the specified license, such as `standard` or `enhanced`; prepending a `-` sign excludes results from that license<br><br>**Constraints**: *Pattern*: `^.+$` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 200` |
| `sort` | [`*models.Sort1Enum`](../../doc/models/sort-1-enum.md) | Query, Optional | Sort order<br><br>**Default**: `"newest"` |
| `username` | `*string` | Query, Optional | Filter licenses by username of licensee<br><br>**Constraints**: *Pattern*: `^.+$` |
| `startDate` | `*time.Time` | Query, Optional | Show licenses created on or after the specified date |
| `endDate` | `*time.Time` | Query, Optional | Show licenses created before the specified date |
| `licenseId` | `*string` | Query, Optional | Filter by the license ID<br><br>**Constraints**: *Pattern*: `^.+$` |
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

sfxId := "12345678"

license := "standard"

page := 1

perPage := 20

sort := models.Sort1Enum_NEWEST

username := "aUniqueUsername"

startDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

endDate := parseTime(time.RFC3339, "03/29/2021 13:25:13", func(err error) { log.Fatalln(err) })

downloadAvailability := models.DownloadAvailabilityEnum_ALL

teamHistory := false

apiResponse, err := soundEffectsController.GetSfxLicenseList(ctx, &sfxId, &license, &page, &perPage, &sort, &username, &startDate, &endDate, nil, &downloadAvailability, &teamHistory)
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


# Licenses SFX

This endpoint licenses sounds effect assets.

```go
LicensesSFX(
    ctx context.Context,
    body models.LicenseSFXRequest) (
    models.ApiResponse[models.LicenseSFXResultDataList],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.LicenseSFXRequest`](../../doc/models/license-sfx-request.md) | Body, Required | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.LicenseSFXResultDataList](../../doc/models/license-sfx-result-data-list.md).

## Example Usage

```go
ctx := context.Background()

body := models.LicenseSFXRequest{
    SoundEffects:         []models.LicenseSFX{
        models.LicenseSFX{
            Format:               models.ToPointer(models.Format3Enum_WAV),
            SfxId:                "123456789",
            SubscriptionId:       "s12345678",
        },
    },
}

apiResponse, err := soundEffectsController.LicensesSFX(ctx, body)
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


# Download Sfx

This endpoint redownloads sound effects that you have already received a license for. The download links in the response are valid for 8 hours.

```go
DownloadSfx(
    ctx context.Context,
    id string) (
    models.ApiResponse[models.SfxUrl],
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

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.SfxUrl](../../doc/models/sfx-url.md).

## Example Usage

```go
ctx := context.Background()

id := "123"

apiResponse, err := soundEffectsController.DownloadSfx(ctx, id)
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
  "url": "http://download.dev.shutterstock.com/gatekeeper/abc/shutterstock_id.wav"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiError` |
| 401 | Unauthorized | `ApiError` |
| 403 | Forbidden | `ApiError` |


# Search SFX

This endpoint searches for sound effects. If you specify more than one search parameter, the API uses an AND condition.

```go
SearchSFX(
    ctx context.Context,
    addedDate *time.Time,
    addedDateStart *time.Time,
    addedDateEnd *time.Time,
    duration *int,
    durationFrom *int,
    durationTo *int,
    page *int,
    perPage *int,
    query *string,
    safe *bool,
    sort *models.Sort21Enum,
    view *models.View1Enum,
    language *models.LanguageEnum) (
    models.ApiResponse[models.SFXSearchResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `addedDate` | `*time.Time` | Query, Optional | Show sound effects added on the specified date |
| `addedDateStart` | `*time.Time` | Query, Optional | Show sound effects added on or after the specified date |
| `addedDateEnd` | `*time.Time` | Query, Optional | Show sound effects added before the specified date |
| `duration` | `*int` | Query, Optional | Show sound effects with the specified duration in seconds |
| `durationFrom` | `*int` | Query, Optional | Show sound effects with the specified duration or longer in seconds |
| `durationTo` | `*int` | Query, Optional | Show sound effects with the specified duration or shorter in seconds |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 500` |
| `query` | `*string` | Query, Optional | One or more search terms separated by spaces |
| `safe` | `*bool` | Query, Optional | Enable or disable safe search<br><br>**Default**: `true` |
| `sort` | [`*models.Sort21Enum`](../../doc/models/sort-21-enum.md) | Query, Optional | Sort by<br><br>**Default**: `"popular"` |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Set query and result language (uses Accept-Language header if not set) |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.SFXSearchResults](../../doc/models/sfx-search-results.md).

## Example Usage

```go
ctx := context.Background()

addedDate := parseTime(time.RFC3339, "2022-09-23", func(err error) { log.Fatalln(err) })

addedDateStart := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

addedDateEnd := parseTime(time.RFC3339, "2021-03-29", func(err error) { log.Fatalln(err) })

duration := 180

durationFrom := 30

durationTo := 180

page := 1

perPage := 1

query := "drum"

safe := true

sort := models.Sort21Enum_POPULAR

view := models.View1Enum_FULL

language := models.LanguageEnum_CS

apiResponse, err := soundEffectsController.SearchSFX(ctx, &addedDate, &addedDateStart, &addedDateEnd, &duration, &durationFrom, &durationTo, &page, &perPage, &query, &safe, &sort, &view, &language)
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


# Get Sfx Details

This endpoint shows information about a sound effect.

```go
GetSfxDetails(
    ctx context.Context,
    id int,
    language *models.LanguageEnum,
    view *models.View1Enum,
    library *models.Library1Enum,
    searchId *string) (
    models.ApiResponse[models.SFX],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `int` | Template, Required | Audio track ID |
| `language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Query, Optional | Language for the keywords and categories in the response |
| `view` | [`*models.View1Enum`](../../doc/models/view-1-enum.md) | Query, Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `library` | [`*models.Library1Enum`](../../doc/models/library-1-enum.md) | Query, Optional | Which library to fetch from |
| `searchId` | `*string` | Query, Optional | The ID of the search that is related to this request |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.SFX](../../doc/models/sfx.md).

## Example Usage

```go
ctx := context.Background()

id := 442583

language := models.LanguageEnum_CS

view := models.View1Enum_FULL

library := models.Library1Enum_SHUTTERSTOCK

searchId := "00000000-0000-0000-0000-000000000000"

apiResponse, err := soundEffectsController.GetSfxDetails(ctx, id, &language, &view, &library, &searchId)
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

