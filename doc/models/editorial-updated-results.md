
# Editorial Updated Results

Editorial updated results

## Structure

`EditorialUpdatedResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.EditorialUpdatedContent`](../../doc/models/editorial-updated-content.md) | Required | Editorial updated items |
| `Message` | `*string` | Optional | Optional error message |
| `Next` | `*string` | Optional | Cursor value that represents the next page of results |
| `PerPage` | `*int` | Optional | Number of results per page |
| `Prev` | `*string` | Optional | Cursor value that represents the previous page of results |

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
    editorialUpdatedResults := models.EditorialUpdatedResults{
        Data:                 []models.EditorialUpdatedContent{
            models.EditorialUpdatedContent{
                Aspect:               models.ToPointer(float64(1.481)),
                Assets:               models.ToPointer(models.EditorialAssets{
                    MediumJpg:            models.ToPointer(models.ImageSizeDetails{
                        DisplayName:          models.ToPointer("Med"),
                        Dpi:                  models.ToPointer(6),
                        FileSize:             models.ToPointer(254),
                        Format:               models.ToPointer("format4"),
                        Height:               models.ToPointer(675),
                        IsLicensable:         models.ToPointer(true),
                        Width:                models.ToPointer(1000),
                    }),
                    Original:             models.ToPointer(models.ImageSizeDetails{
                        DisplayName:          models.ToPointer("Original"),
                        Dpi:                  models.ToPointer(44),
                        FileSize:             models.ToPointer(36),
                        Format:               models.ToPointer("format6"),
                        Height:               models.ToPointer(3263),
                        IsLicensable:         models.ToPointer(true),
                        Width:                models.ToPointer(4831),
                    }),
                    SmallJpg:             models.ToPointer(models.ImageSizeDetails{
                        DisplayName:          models.ToPointer("Small"),
                        Dpi:                  models.ToPointer(100),
                        FileSize:             models.ToPointer(92),
                        Format:               models.ToPointer("format8"),
                        Height:               models.ToPointer(337),
                        IsLicensable:         models.ToPointer(true),
                        Width:                models.ToPointer(500),
                    }),
                    Thumb170:             models.ToPointer(models.Thumbnail{
                        Height:               115,
                        Url:                  "https://editorial01.shutterstock.com/thumb/9804979n/c4377a53/Shutterstock_9804979n.jpg",
                        Width:                170,
                    }),
                    Thumb220:             models.ToPointer(models.Thumbnail{
                        Height:               149,
                        Url:                  "https://editorial01.shutterstock.com/thumb-220/9804979n/c57a68c7/Shutterstock_9804979n.jpg",
                        Width:                220,
                    }),
                    Watermark1500:        models.ToPointer(models.Thumbnail{
                        Height:               1500,
                        Url:                  "https://editorial01.shutterstock.com/wm-preview-1500/9933285a/ab82fea4/Shutterstock_9933285a.jpg",
                        Width:                1040,
                    }),
                    Watermark450:         models.ToPointer(models.Thumbnail{
                        Height:               304,
                        Url:                  "https://editorial01.shutterstock.com/wm-preview-450/9804979n/37d19dce/Shutterstock_9804979n.jpg",
                        Width:                450,
                    }),
                }),
                Byline:               models.ToPointer("ALEX HOFFORD/EPA-EFE/Shutterstock"),
                Caption:              models.ToPointer(""),
                Categories:           []models.EditorialCategory{
                },
                CommercialStatus:     models.ToPointer(models.CommercialStatus{
                    Status:               models.ToPointer("available"),
                }),
                DateTaken:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2018-08-24", func(err error) { log.Fatalln(err) })),
                Description:          models.ToPointer("Members of the TyLoo e-Sports team from China prepare to face off against the Kinguin e-Sports team from Poland at the ICBC (Asia) e-Sports and Music Festival Hong Kong 2018, Hong Kong, China, 24 August 2018. The festival runs from 24 to 26 August with professional gamers from around the world competing in international e-sports tournaments."),
                Id:                   "9804979n",
                Keywords:             []string{
                },
                Rights:               models.ToPointer(models.Rights{
                    Countries:            models.ToPointer("CAN,+DEU,+GBR,+USA,-*"),
                }),
                SupplierCode:         models.ToPointer("EPA"),
                Title:                models.ToPointer("Hong Kong kicks off international e-Sports competition, China - 24 Aug 2018"),
                UpdatedTime:          models.ToPointer(parseTime(time.RFC3339, "2019-07-15T20:04:44-04:00", func(err error) { log.Fatalln(err) })),
                Updates:              []string{
                    "addition",
                },
            },
        },
        Message:              models.ToPointer("message8"),
        Next:                 models.ToPointer("eyJ2IjoxLCJzIjoxfQ=="),
        PerPage:              models.ToPointer(1),
        Prev:                 models.ToPointer(""),
    }

}
```

