# Custom Music

```go
customMusicController := client.CustomMusicController()
```

## Class Name

`CustomMusicController`

## Methods

* [List Custom Descriptors](../../doc/controllers/custom-music.md#list-custom-descriptors)
* [List Custom Instruments](../../doc/controllers/custom-music.md#list-custom-instruments)
* [Fetch Renders](../../doc/controllers/custom-music.md#fetch-renders)
* [Create Audio Renders](../../doc/controllers/custom-music.md#create-audio-renders)


# List Custom Descriptors

This endpoint lists the descriptors that you can use in the audio regions in an audio render.

```go
ListCustomDescriptors(
    ctx context.Context,
    renderSpeedOver *float64,
    bandId *string,
    bandName *string,
    page *int,
    perPage *int,
    id []string,
    instrumentName *string,
    instrumentId *string,
    tempo *float64,
    tempoTo *float64,
    tempoFrom *float64,
    name *string,
    tag *string) (
    models.ApiResponse[models.DescriptorsListResult],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `renderSpeedOver` | `*float64` | Query, Optional | Show descriptors with an average render speed that is greater than or equal to the specified value |
| `bandId` | `*string` | Query, Optional | Show descriptors that contain the specified band (case-sentsitive) |
| `bandName` | `*string` | Query, Optional | Show descriptors with the specified band name (case-sensitive) |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 100` |
| `id` | `[]string` | Query, Optional | Show descriptors with the specified IDs (case-sensitive)<br><br>**Constraints**: *Maximum Items*: `20` |
| `instrumentName` | `*string` | Query, Optional | Show descriptors with the specified instrument name (case-sensitive) |
| `instrumentId` | `*string` | Query, Optional | Show descriptors with the specified instrument ID (case-sensitive) |
| `tempo` | `*float64` | Query, Optional | Show descriptors whose tempo range includes the specified tempo in beats per minute |
| `tempoTo` | `*float64` | Query, Optional | Show descriptors with a tempo that is less than or equal to the specified number |
| `tempoFrom` | `*float64` | Query, Optional | Show descriptors that have a tempo range that includes the specified tempo in beats per minute |
| `name` | `*string` | Query, Optional | Show descriptors with the specified name (case-sensitive) |
| `tag` | `*string` | Query, Optional | Show descriptors with the specified tag, such as Cinematic or Roomy (case-sensitive) |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.DescriptorsListResult](../../doc/models/descriptors-list-result.md).

## Example Usage

```go
ctx := context.Background()

renderSpeedOver := float64(5)

bandId := "Corporate Folk Bonfire Band 1"

bandName := "Documentary Underscore Heartfelt Band 1"

page := 1

perPage := 1

instrumentName := "Precision Bass - Full"

instrumentId := "direct_fluorescent_synth_lead"

tempo := float64(90)

tempoTo := float64(120)

tempoFrom := float64(60)

name := "Corporate Pop Inspirational High Energy"

tag := "Cinematic"

apiResponse, err := customMusicController.ListCustomDescriptors(ctx, &renderSpeedOver, &bandId, &bandName, &page, &perPage, nil, &instrumentName, &instrumentId, &tempo, &tempoTo, &tempoFrom, &name, &tag)
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


# List Custom Instruments

This endpoint lists the instruments that you can include in computer audio. If you specify more than one search parameter, the API uses an AND condition.

```go
ListCustomInstruments(
    ctx context.Context,
    id []string,
    perPage *int,
    page *int,
    name *string,
    tag *string) (
    models.ApiResponse[models.InstrumentsListResult],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Optional | Show instruments with the specified ID |
| `perPage` | `*int` | Query, Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `*int` | Query, Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `name` | `*string` | Query, Optional | Show instruments with the specified name (case-sensitive) |
| `tag` | `*string` | Query, Optional | Show instruments with the specified tag, such as Percussion or Strings (case-sensitive) |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.InstrumentsListResult](../../doc/models/instruments-list-result.md).

## Example Usage

```go
ctx := context.Background()

perPage := 1

page := 1

name := "Precision Bass - Full"

tag := "Percussion"

apiResponse, err := customMusicController.ListCustomInstruments(ctx, nil, &perPage, &page, &name, &tag)
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


# Fetch Renders

This endpoint shows the status of one or more audio renders, including download links for completed audio.

```go
FetchRenders(
    ctx context.Context,
    id []string) (
    models.ApiResponse[models.AudioRendersListResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `[]string` | Query, Required | One or more render IDs |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.AudioRendersListResults](../../doc/models/audio-renders-list-results.md).

## Example Usage

```go
ctx := context.Background()

id := []string{
    "L2w7h9VNFlkzpllSUunSYayenKjN",
    "BeHx3UNXzMBB4dGsC9aa6VxnpcWl",
}

apiResponse, err := customMusicController.FetchRenders(ctx, id)
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


# Create Audio Renders

This endpoint creates rendered audio from timeline data. It returns a render ID that you can use to download the finished audio when it is ready. The render ID is valid for up to 48 hours.

```go
CreateAudioRenders(
    ctx context.Context,
    body models.CreateAudioRendersRequest) (
    models.ApiResponse[models.AudioRendersListResults],
    error)
```

## Authentication

This endpoint requires [basic](../../doc/auth/basic-authentication.md) **OR** [customer_accessCode](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`models.CreateAudioRendersRequest`](../../doc/models/create-audio-renders-request.md) | Body, Required | Parameters for the audio, including the timeline and information about the output file |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [models.AudioRendersListResults](../../doc/models/audio-renders-list-results.md).

## Example Usage

```go
ctx := context.Background()

body := models.CreateAudioRendersRequest{
    AudioRenders:         []models.CreateAudioRender{
        models.CreateAudioRender{
            Filename:             "My Project.mp3",
            Preset:               models.Preset1Enum_MASTERMP3,
            Timeline:             models.AudioRenderTimeline{
                Spans:                []models.AudioRenderTimelineSpan{
                    models.AudioRenderTimelineSpan{
                        Id:                   models.ToPointer(float64(111)),
                        InstrumentGroups:     []models.AudioRenderTimelineSpanInstrumentGroup{
                            models.AudioRenderTimelineSpanInstrumentGroup{
                                InstrumentGroup:      "roomy_kit",
                                Statuses:             []models.AudioRenderTimelineSpanInstrumentGroupStatus{
                                    models.AudioRenderTimelineSpanInstrumentGroupStatus{
                                        Beat:                 float64(12),
                                        Status:               models.Status1Enum_ACTIVE,
                                    },
                                },
                            },
                        },
                        Regions:              []models.AudioRenderTimelineSpanRegion{
                            models.AudioRenderTimelineSpanRegion{
                                Beat:                 12,
                                Descriptor:           "cinematic_minimal_tense",
                                EndType:              models.ToPointer(models.EndType{
                                    Beat:                 float64(24),
                                    Event:                models.EventEnum_ENDING,
                                    Type:                 models.TypeEnum_RINGOUT,
                                }),
                                Id:                   float64(222),
                                Key:                  models.ToPointer(models.Key{
                                    TonicNote:            models.ToPointer(models.TonicNoteEnum_C),
                                    TonicQuality:         models.ToPointer(models.TonicQualityEnum_MAJOR),
                                }),
                                Region:               models.RegionEnum_MUSIC,
                            },
                        },
                        SpanType:             models.SpanTypeEnum_METERED,
                        Tempo:                models.ToPointer(76),
                        TempoChanges:         []models.AudioRenderTimelineSpanTempoChanges{
                            models.AudioRenderTimelineSpanTempoChanges{
                                Tempo:                float64(86),
                                Time:                 float64(5),
                            },
                        },
                        Time:                 5,
                    },
                    models.AudioRenderTimelineSpan{
                        SpanType:             models.SpanTypeEnum_UNMETERED,
                        Time:                 20,
                    },
                },
            },
        },
    },
}

apiResponse, err := customMusicController.CreateAudioRenders(ctx, body)
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
  "audio_renders": [
    {
      "created_date": "2021-01-26T12:10:22-05:00",
      "files": [],
      "id": "njlpYoWWmb1AYs2nZyw7EcNWbAkZ",
      "preset": "MASTER_MP3",
      "progress_percent": 0,
      "status": "WAITING_COMPOSE",
      "timeline": {},
      "updated_date": "2021-01-26T13:10:22-05:00"
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

