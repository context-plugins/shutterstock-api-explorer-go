
# Basic Authentication



Documentation for accessing and setting credentials for basic.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| username | `string` | The username to use with basic authentication | `WithUsername` | `Username()` |
| password | `string` | The password to use with basic authentication | `WithPassword` | `Password()` |



**Note:** Required auth credentials can be set using `WithBasicCredentials()` by providing a credentials instance with `NewBasicCredentials()` in the configuration initialization and accessed using the `BasicCredentials()` method in the configuration instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```go
package main

import (
    "shutterstockapiexplorer"
)

func main() {
    client := shutterstockapiexplorer.NewClient(
    shutterstockapiexplorer.CreateConfiguration(
            shutterstockapiexplorer.WithBasicCredentials(
                shutterstockapiexplorer.NewBasicCredentials(
                    "Username",
                    "Password",
                ),
            ),
        ),
    )
}
```


