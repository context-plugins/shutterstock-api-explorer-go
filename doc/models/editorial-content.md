
# Editorial Content

Metadata about editorial content

## Structure

`EditorialContent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Aspect` | `*float64` | Optional | - |
| `Assets` | [`*models.EditorialAssets`](../../doc/models/editorial-assets.md) | Optional | Asset information, including size and thumbnail URLs |
| `Byline` | `*string` | Optional | - |
| `Caption` | `*string` | Optional | - |
| `Categories` | [`[]models.EditorialCategory`](../../doc/models/editorial-category.md) | Optional | List of categories |
| `DateTaken` | `*time.Time` | Optional | - |
| `Description` | `*string` | Optional | - |
| `Id` | `string` | Required | - |
| `Keywords` | `[]string` | Optional | - |
| `SpecialInstructions` | `*string` | Optional | - |
| `Title` | `*string` | Optional | - |

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
    editorialContent := models.EditorialContent{
        Aspect:               models.ToPointer(float64(1.621)),
        Assets:               models.ToPointer(models.EditorialAssets{
            MediumJpg:            models.ToPointer(models.ImageSizeDetails{
                DisplayName:          models.ToPointer("Med"),
                Dpi:                  models.ToPointer(6),
                FileSize:             models.ToPointer(254),
                Format:               models.ToPointer("format4"),
                Height:               models.ToPointer(617),
                IsLicensable:         models.ToPointer(true),
                Width:                models.ToPointer(1000),
            }),
            Original:             models.ToPointer(models.ImageSizeDetails{
                DisplayName:          models.ToPointer("Original"),
                Dpi:                  models.ToPointer(44),
                FileSize:             models.ToPointer(36),
                Format:               models.ToPointer("format6"),
                Height:               models.ToPointer(3693),
                IsLicensable:         models.ToPointer(true),
                Width:                models.ToPointer(5985),
            }),
            SmallJpg:             models.ToPointer(models.ImageSizeDetails{
                DisplayName:          models.ToPointer("Small"),
                Dpi:                  models.ToPointer(100),
                FileSize:             models.ToPointer(92),
                Format:               models.ToPointer("format8"),
                Height:               models.ToPointer(309),
                IsLicensable:         models.ToPointer(true),
                Width:                models.ToPointer(500),
            }),
            Thumb170:             models.ToPointer(models.Thumbnail{
                Height:               105,
                Url:                  "https://editorial01.qa.shuttercorp.net/thumb/10687730b/272a999e/Shutterstock_10687730b.jpg",
                Width:                170,
            }),
            Thumb220:             models.ToPointer(models.Thumbnail{
                Height:               136,
                Url:                  "https://editorial01.qa.shuttercorp.net/thumb-220/10687730b/927a6ebe/Shutterstock_10687730b.jpg",
                Width:                220,
            }),
            Watermark1500:        models.ToPointer(models.Thumbnail{
                Height:               926,
                Url:                  "https://editorial01.qa.shuttercorp.net/wm-preview-1500/10687730b/ee2d7ae1/Shutterstock_10687730b.jpg",
                Width:                1500,
            }),
            Watermark450:         models.ToPointer(models.Thumbnail{
                Height:               278,
                Url:                  "https://editorial01.qa.shuttercorp.net/wm-preview-450/10687730b/ff2443ad/Shutterstock_10687730b.jpg",
                Width:                450,
            }),
        }),
        Byline:               models.ToPointer("Jon Super/AP/Shutterstock"),
        Caption:              models.ToPointer(""),
        Categories:           []models.EditorialCategory{
            models.EditorialCategory{
                Name:                 models.ToPointer("Sport"),
            },
        },
        DateTaken:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2021-05-11", func(err error) { log.Fatalln(err) })),
        Description:          models.ToPointer("Security and stewards stand outside the Old Trafford stadium in Manchester, England, ahead of the English Premier League soccer match between Manchester United and Leicester City. This is the first Manchester United home match since fans protested against American owner Joel Glazer, forcing the postponement of the team's Premier League game against Liverpool. The protests prompted Glazer to publish a letter in which he pledged to accelerate discussions with fans about supporters being able to have a greater say at the club"),
        Id:                   "10687730b",
        Keywords:             []string{
            "england",
            "europe",
            "leicester city fc",
            "manchester",
            "manchester united fc",
            "men's soccer",
            "men's sports",
            "premier league",
            "professional soccer",
            "soccer",
            "sports",
            "united kingdom",
            "western europe",
            "wsoc",
        },
        Title:                models.ToPointer("Soccer Premier League, Manchester, United Kingdom - 11 May 2021"),
    }

}
```

