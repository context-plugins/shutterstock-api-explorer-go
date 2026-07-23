
# Download History User Details

Information about a user

## Structure

`DownloadHistoryUserDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Username` | `string` | Required | The name of the user who downloaded the item |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    downloadHistoryUserDetails := models.DownloadHistoryUserDetails{
        Username:             "jdoe",
    }

}
```

