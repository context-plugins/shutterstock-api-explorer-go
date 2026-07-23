
# Download History Media Details

Information about the downloaded media

## Structure

`DownloadHistoryMediaDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Format` | [`*models.DownloadHistoryFormatDetails`](../../doc/models/download-history-format-details.md) | Optional | Information about the format of a download |
| `Id` | `string` | Required | ID of the download history media details |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    downloadHistoryMediaDetails := models.DownloadHistoryMediaDetails{
        Format:               models.ToPointer(models.DownloadHistoryFormatDetails{
            Format:               models.ToPointer("jpg"),
            Size:                 models.ToPointer("medium"),
        }),
        Id:                   "1234567",
    }

}
```

