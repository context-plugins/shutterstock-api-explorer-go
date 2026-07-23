
# Download History Format Details

Information about the format of a download

## Structure

`DownloadHistoryFormatDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Format` | `*string` | Optional | The format of the downloaded media |
| `Size` | `*string` | Optional | The size of the downloaded media |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    downloadHistoryFormatDetails := models.DownloadHistoryFormatDetails{
        Format:               models.ToPointer("jpg"),
        Size:                 models.ToPointer("medium"),
    }

}
```

