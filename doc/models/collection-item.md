
# Collection Item

Metadata about an item that is part of a collection

## Structure

`CollectionItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AddedTime` | `*time.Time` | Optional | The date the item was added to the collection |
| `Id` | `string` | Required | ID of the item |
| `MediaType` | `*string` | Optional | The media type of the item, such as image, video, or audio |

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
    collectionItem := models.CollectionItem{
        AddedTime:            models.ToPointer(parseTime(time.RFC3339, "2020-05-29T12:10:22-05:00", func(err error) { log.Fatalln(err) })),
        Id:                   "1690105108",
        MediaType:            models.ToPointer("image"),
    }

}
```

