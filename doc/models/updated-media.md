
# Updated Media

Information about a piece of updated media

## Structure

`UpdatedMedia`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `string` | Required | ID of the media |
| `UpdatedTime` | `time.Time` | Required | Date that the media was updated |
| `Updates` | `[]string` | Required | Types of updates that were made to the piece of media |

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
    updatedMedia := models.UpdatedMedia{
        Id:                   "123456789",
        UpdatedTime:          parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) }),
        Updates:              []string{
            "addition",
            "edit",
        },
    }

}
```

