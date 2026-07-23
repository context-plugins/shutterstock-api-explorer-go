
# Getting Started with Shutterstock API Explorer

## Introduction

The Shutterstock API provides access to Shutterstock's library of media, as well as information about customers' accounts and the contributors that provide the media.

### Requirements

The SDK requires **Go version 1.18 or above**.

## Building

### Install Dependencies

Resolve all the SDK dependencies, using the `go get` command.

## Installation

The following section explains how to use the shutterstockapiexplorer library in a new project.

### 1. Add SDK as a Dependency to the Application

- Add the following lines to your application's `go.mod` file:

```go
replace shutterstockapiexplorer => ".\\shutterstock-api-explorer-go_generic_lib" // local path to the SDK

require shutterstockapiexplorer v0.0.0
```

- Resolve the dependencies in the updated `go.mod` file, using the `go get` command.

## Test the SDK

`Go Testing` is used as the testing framework. To run the unit tests of the SDK, navigate to the root directory of the SDK and run the following command in the terminal:

```bash
$ go test
```

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| httpConfiguration | [`HttpConfiguration`](doc/http-configuration.md) | Configurable http client options like timeout and retries. |
| basicCredentials | [`BasicCredentials`](doc/auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |
| customerAccessCodeCredentials | [`CustomerAccessCodeCredentials`](doc/auth/oauth-2-authorization-code-grant.md) | The Credentials Setter for OAuth 2 Authorization Code Grant |

The API client can be initialized as follows:

```go
package main

import (
    "shutterstockapiexplorer"
    "shutterstockapiexplorer/models"
)

func main() {
    client := shutterstockapiexplorer.NewClient(
    shutterstockapiexplorer.CreateConfiguration(
            shutterstockapiexplorer.WithHttpConfiguration(
                shutterstockapiexplorer.CreateHttpConfiguration(
                    shutterstockapiexplorer.WithTimeout(0),
                ),
            ),
            shutterstockapiexplorer.WithEnvironment(shutterstockapiexplorer.PRODUCTION),
            shutterstockapiexplorer.WithBasicCredentials(
                shutterstockapiexplorer.NewBasicCredentials(
                    "Username",
                    "Password",
                ),
            ),
            shutterstockapiexplorer.WithCustomerAccessCodeCredentials(
                shutterstockapiexplorer.NewCustomerAccessCodeCredentials(
                    "OAuthClientId",
                    "OAuthClientSecret",
                    "OAuthRedirectUri",
                ).
                WithOAuthScopes([]models.OAuthScopeCustomerAccessCodeEnum{
        models.OAuthScopeCustomerAccessCodeEnum_COLLECTIONSEDIT,
        models.OAuthScopeCustomerAccessCodeEnum_COLLECTIONSVIEW,
    }),
            ),
        ),
    )
}
```

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| PRODUCTION | **Default** Live server |
| ENVIRONMENT2 | Sandbox server |

## Authorization

This API uses the following authentication schemes.

* [`basic (Basic Authentication)`](doc/auth/basic-authentication.md)
* [`customer_accessCode (OAuth 2 Authorization Code Grant)`](doc/auth/oauth-2-authorization-code-grant.md)

## List of APIs

* [Custom Music](doc/controllers/custom-music.md)
* [Audio](doc/controllers/audio.md)
* [Images](doc/controllers/images.md)
* [Catalog](doc/controllers/catalog.md)
* [Contributors](doc/controllers/contributors.md)
* [Computer Vision](doc/controllers/computer-vision.md)
* [Editorial Images](doc/controllers/editorial-images.md)
* [Editorial Video](doc/controllers/editorial-video.md)
* [Oauth](doc/controllers/oauth.md)
* [Sound Effects](doc/controllers/sound-effects.md)
* [Test](doc/controllers/test.md)
* [Users](doc/controllers/users.md)
* [Videos](doc/controllers/videos.md)

## SDK Infrastructure

### Configuration

* [HttpConfiguration](doc/http-configuration.md)
* [RetryConfiguration](doc/retry-configuration.md)

### Utilities

* [ApiResponse](doc/api-response.md)

