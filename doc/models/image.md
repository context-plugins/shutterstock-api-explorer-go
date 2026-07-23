
# Image

Information about an image

## Structure

`Image`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AddedDate` | `*time.Time` | Optional | Date that the image was added by the contributor |
| `AffiliateUrl` | `*string` | Optional | Affiliate referral link; appears only for registered affiliate partners |
| `Aspect` | `*float64` | Optional | Aspect ratio of the image in decimal format, such as 0.6667 |
| `Assets` | [`*models.ImageAssets`](../../doc/models/image-assets.md) | Optional | Information about the assets that are part of an image |
| `Categories` | [`[]models.Category`](../../doc/models/category.md) | Optional | Categories that this image is a part of |
| `Contributor` | [`models.Contributor`](../../doc/models/contributor.md) | Required | Information about a contributor |
| `Description` | `*string` | Optional | Detailed description of the image |
| `HasModelRelease` | `*bool` | Optional | Indicates whether there are model releases for the image |
| `HasPropertyRelease` | `*bool` | Optional | Indicates whether there are property releases for the image |
| `Id` | `string` | Required | Image ID |
| `ImageType` | `*string` | Optional | Type of image |
| `Insights` | [`*models.Insights2`](../../doc/models/insights-2.md) | Optional | AI-powered insights about how the asset will perform for the objective and audience |
| `IsAdult` | `*bool` | Optional | Whether or not this image contains adult content |
| `IsEditorial` | `*bool` | Optional | Whether or not this image is editorial content |
| `IsIllustration` | `*bool` | Optional | Whether or not this image is an illustration |
| `Keywords` | `[]string` | Optional | Keywords associated with the content of this image |
| `MediaType` | `string` | Required | Media type of this image, should always be "image" |
| `ModelReleases` | [`[]models.ModelRelease`](../../doc/models/model-release.md) | Optional | List of model releases |
| `Models` | [`[]models.Model`](../../doc/models/model.md) | Optional | List of models |
| `Releases` | `[]string` | Optional | List of all releases of this image |
| `Url` | `*string` | Optional | Link to image information page; included only for certain accounts |

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
    image := models.Image{
        AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
        AffiliateUrl:         models.ToPointer("affiliate_url2"),
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
    }

}
```

