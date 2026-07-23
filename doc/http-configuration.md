
# HttpConfiguration

The following parameters are configurable for the HttpConfiguration:

## Properties

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| timeout | `float64` | Timeout in seconds.<br>*Default*: `0` | `WithTimeout` | `Timeout()` |
| transport | `httpRoundTripper` | Establishes network connection and caches them for reuse.<br>*Default*: `http.DefaultTransport` | `WithTransport` | `Transport()` |
| retryConfiguration | [`shutterstockapiexplorerRetryConfiguration`](../doc/retry-configuration.md) | Configurations to retry requests.<br>*Default*: `shutterstockapiexplorer.DefaultRetryConfiguration()` | `WithRetryConfiguration` | `RetryConfiguration()` |

The httpConfiguration can be initialized as follows:

```go
package main

import (
    "shutterstockapiexplorer"
    "net/http"
)

func main() {
    httpConfiguration := shutterstockapiexplorer.CreateHttpConfiguration(
        shutterstockapiexplorer.WithTimeout(0),
        shutterstockapiexplorer.WithTransport(http.DefaultTransport),
        shutterstockapiexplorer.WithRetryConfiguration(shutterstockapiexplorer.DefaultRetryConfiguration()),
    )
}
```

