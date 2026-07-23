
# Allotment

An allotment of credits as part of a subscription

## Structure

`Allotment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `DownloadsLeft` | `*int` | Optional | Number of credits remaining in the subscription |
| `DownloadsLimit` | `*int` | Optional | Total number of credits available to this subscription |
| `EndTime` | `*time.Time` | Optional | Date the subscription ends |
| `StartTime` | `*time.Time` | Optional | Date the subscription started |

## Example

```go
package main

import (
    "log"
    "time"
    "shutterstockapiexplorer/models"
)

func main() {
    parseTime := func(layout, value string, errCallback func(error)) time.Time {
        dateTime, err := time.Parse(layout, value)
        if err != nil {
            errCallback(err) 
       }
        return dateTime
    }
    allotment := models.Allotment{
        DownloadsLeft:        models.ToPointer(5),
        DownloadsLimit:       models.ToPointer(10),
        EndTime:              models.ToPointer(parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) })),
        StartTime:            models.ToPointer(parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) })),
    }

}
```

