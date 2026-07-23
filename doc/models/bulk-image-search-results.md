
# Bulk Image Search Results

List of search results for each given query

## Structure

`BulkImageSearchResults`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `BulkSearchId` | `*string` | Optional | Unique identifier for the search request |
| `Results` | [`[]models.ImageSearchResults`](../../doc/models/image-search-results.md) | Optional | List of image search results |

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
    bulkImageSearchResults := models.BulkImageSearchResults{
        BulkSearchId:         models.ToPointer("bulk_search_id0"),
        Results:              []models.ImageSearchResults{
            models.ImageSearchResults{
                Data:                 []models.Image{
                    models.Image{
                        AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
                        AffiliateUrl:         models.ToPointer("affiliate_url6"),
                        Aspect:               models.ToPointer(float64(1.5)),
                        Assets:               models.ToPointer(models.ImageAssets{
                            HugeJpg:              nil,
                            HugeThumb:            models.ToPointer(models.Thumbnail{
                                Height:               260,
                                Url:                  "https://image.shutterstock.com/image-photo/cropped-image-woman-gardening-260nw-1572478477.jpg",
                                Width:                390,
                            }),
                            LargeThumb:           models.ToPointer(models.Thumbnail{
                                Height:               100,
                                Url:                  "https://thumb7.shutterstock.com/thumb_large/250738318/1572478477/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
                                Width:                150,
                            }),
                            MediumJpg:            nil,
                            Preview:              models.ToPointer(models.Thumbnail{
                                Height:               300,
                                Url:                  "https://image.shutterstock.com/display_pic_with_logo/250738318/1572478477/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
                                Width:                450,
                            }),
                            Preview1000:          models.ToPointer(models.Thumbnail{
                                Height:               667,
                                Url:                  "https://ak.picdn.net/shutterstock/photos/1572478477/watermark_1000/1706028c641ea2f443057287c67d9b91/preview_1000-1572478477.jpg",
                                Width:                1000,
                            }),
                            Preview1500:          models.ToPointer(models.Thumbnail{
                                Height:               1000,
                                Url:                  "https://image.shutterstock.com/z/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
                                Width:                1500,
                            }),
                            SmallThumb:           models.ToPointer(models.Thumbnail{
                                Height:               67,
                                Url:                  "https://thumb7.shutterstock.com/thumb_small/250738318/1572478477/stock-photo-cropped-image-of-woman-gardening-1572478477.jpg",
                                Width:                100,
                            }),
                        }),
                        Categories:           []models.Category{
                            models.Category{
                                Id:                   models.ToPointer("id8"),
                                Name:                 models.ToPointer("name8"),
                            },
                            models.Category{
                                Id:                   models.ToPointer("id8"),
                                Name:                 models.ToPointer("name8"),
                            },
                            models.Category{
                                Id:                   models.ToPointer("id8"),
                                Name:                 models.ToPointer("name8"),
                            },
                        },
                        Contributor:          models.Contributor{
                            Id:                   "250738318",
                        },
                        Description:          models.ToPointer("cropped image of woman gardening"),
                        HasModelRelease:      models.ToPointer(true),
                        Id:                   "1572478477",
                        ImageType:            models.ToPointer("photo"),
                        MediaType:            "image",
                    },
                },
                Insights:             nil,
                Message:              models.ToPointer("message6"),
                Page:                 models.ToPointer(1),
                PerPage:              models.ToPointer(5),
                SearchId:             "749090bb-2967-4a20-b22e-c800dc845e10",
                SpellcheckInfo:       models.ToPointer(interface{}("")),
                TotalCount:           45,
            },
            models.ImageSearchResults{
                Data:                 []models.Image{
                },
                Insights:             models.ToPointer(models.Insights{
                    LabelPerformance:     nil,
                }),
                Message:              models.ToPointer("message6"),
                Page:                 models.ToPointer(1),
                PerPage:              models.ToPointer(5),
                SearchId:             "749090bb-2967-4a20-b22e-c800dc845e11",
                SpellcheckInfo:       models.ToPointer(interface{}("")),
                TotalCount:           0,
            },
        },
    }

}
```

