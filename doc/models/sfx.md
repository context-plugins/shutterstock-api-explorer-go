
# SFX

SFX metadata

## Structure

`SFX`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AddedDate` | `*time.Time` | Optional | Date this sound effect was added to the Shutterstock library |
| `AffiliateUrl` | `*string` | Optional | Affiliate referral link; appears only for registered affiliate partners |
| `Artist` | `*string` | Optional | Artist of the sound effect |
| `Assets` | [`*models.SFXAssets`](../../doc/models/sfx-assets.md) | Optional | Files that are available as part of an sound effect asset |
| `Contributor` | [`models.Contributor`](../../doc/models/contributor.md) | Required | Information about a contributor |
| `Description` | `*string` | Optional | Description of this sound effect |
| `Duration` | `*float64` | Optional | Duration of this sound effect in seconds |
| `Id` | `string` | Required | Shutterstock ID of this sound effect |
| `Keywords` | `[]string` | Optional | List of all keywords for this sound effect |
| `MediaType` | `string` | Required | Media type of this track; should always be "sfx" |
| `Releases` | `[]string` | Optional | List of all releases of this sound effect |
| `Title` | `*string` | Optional | Title of this sound effect |
| `UpdatedTime` | `*time.Time` | Optional | Time this sound effect was last updated |
| `Url` | `*string` | Optional | - |

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
    sfx := models.SFX{
        AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
        AffiliateUrl:         models.ToPointer("affiliate_url8"),
        Artist:               models.ToPointer("artist0"),
        Assets:               nil,
        Contributor:          models.Contributor{
            Id:                   "1234",
        },
        Description:          models.ToPointer("description8"),
        Id:                   "123",
        MediaType:            "sfx",
    }

}
```

