
# Search Image

Data required to search for an image

## Structure

`SearchImage`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AddedDate` | `*time.Time` | Optional | Show images added on the specified date |
| `AddedDateEnd` | `*time.Time` | Optional | Show images added before the specified date |
| `AddedDateStart` | `*time.Time` | Optional | Show images added on or after the specified date |
| `AspectRatio` | `*float64` | Optional | Show images with the specified aspect ratio, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image |
| `AspectRatioMax` | `*float64` | Optional | Show images with the specified aspect ratio or lower, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `>= 0` |
| `AspectRatioMin` | `*float64` | Optional | Show images with the specified aspect ratio or higher, using a positive decimal of the width divided by the height, such as 1.7778 for a 16:9 image<br><br>**Constraints**: `>= 0` |
| `Authentic` | `*bool` | Optional | Show only authentic images |
| `Category` | `*string` | Optional | Show images with the specified Shutterstock-defined category; specify a category name or ID |
| `Color` | `*string` | Optional | Specify either a hexadecimal color in the format '4F21EA' or 'grayscale'; the API returns images that use similar colors |
| `Contributor` | `[]string` | Optional | Show images with the specified contributor names or IDs, allows multiple |
| `ContributorCountry` | [`*models.SearchImageContributorCountry`](../../doc/models/containers/search-image-contributor-country.md) | Optional | This is a container for one-of cases. |
| `Fields` | `*string` | Optional | Fields to display in the response; see the documentation for the fields parameter in the overview section |
| `Height` | `*int` | Optional | (Deprecated; use height_from and height_to instead) Show images with the specified height |
| `HeightFrom` | `*int` | Optional | Show images with the specified height or larger, in pixels |
| `HeightTo` | `*int` | Optional | Show images with the specified height or smaller, in pixels |
| `ImageType` | [`[]models.ImageTypeEnum`](../../doc/models/image-type-enum.md) | Optional | Show images of the specified type |
| `KeywordSafeSearch` | `*bool` | Optional | Hide results with potentially unsafe keywords<br><br>**Default**: `true` |
| `Language` | [`*models.LanguageEnum`](../../doc/models/language-enum.md) | Optional | Language code |
| `License` | [`[]models.LicenseEnum`](../../doc/models/license-enum.md) | Optional | Show only images with the specified license |
| `Model` | `[]string` | Optional | Show image results with the specified model IDs |
| `Orientation` | [`*models.OrientationEnum`](../../doc/models/orientation-enum.md) | Optional | Show image results with horizontal or vertical orientation |
| `Page` | `*int` | Optional | Page number<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `PeopleAge` | [`*models.PeopleAgeEnum`](../../doc/models/people-age-enum.md) | Optional | Show images that feature people of the specified age category |
| `PeopleEthnicity` | [`[]models.PeopleEthnicityEnum`](../../doc/models/people-ethnicity-enum.md) | Optional | Show images with people of the specified ethnicities, or start with NOT to show images without those ethnicities |
| `PeopleGender` | [`*models.PeopleGenderEnum`](../../doc/models/people-gender-enum.md) | Optional | Show images with people of the specified gender |
| `PeopleModelReleased` | `*bool` | Optional | Show images of people with a signed model release |
| `PeopleNumber` | `*int` | Optional | Show images with the specified number of people<br><br>**Constraints**: `>= 0`, `<= 4` |
| `PerPage` | `*int` | Optional | Number of results per page<br><br>**Default**: `20`<br><br>**Constraints**: `>= 0`, `<= 20` |
| `Query` | `*string` | Optional | One or more search terms separated by spaces; you can use NOT to filter out images that match a term |
| `Region` | [`*models.SearchImageRegion`](../../doc/models/containers/search-image-region.md) | Optional | This is a container for any-of cases. |
| `Safe` | `*bool` | Optional | Enable or disable safe search<br><br>**Default**: `true` |
| `Sort` | [`*models.SortEnum`](../../doc/models/sort-enum.md) | Optional | Sort by<br><br>**Default**: `"popular"` |
| `SpellcheckQuery` | `*bool` | Optional | Spellcheck the search query and return results on suggested spellings<br><br>**Default**: `true` |
| `View` | [`*models.ViewEnum`](../../doc/models/view-enum.md) | Optional | Amount of detail to render in the response<br><br>**Default**: `"minimal"` |
| `Width` | `*int` | Optional | (Deprecated; use width_from and width_to instead) Show images with the specified width |
| `WidthFrom` | `*int` | Optional | Show images with the specified width or larger, in pixels |
| `WidthTo` | `*int` | Optional | Show images with the specified width or smaller, in pixels |

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
    searchImage := models.SearchImage{
        AddedDate:            models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
        AddedDateEnd:         models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
        AddedDateStart:       models.ToPointer(parseTime(models.DEFAULT_DATE, "2016-03-13T12:52:32.123Z", func(err error) { log.Fatalln(err) })),
        AspectRatio:          models.ToPointer(float64(80.36)),
        AspectRatioMax:       models.ToPointer(float64(185.46)),
        License:              []models.LicenseEnum{
            models.LicenseEnum_EDITORIAL,
        },
        Query:                models.ToPointer("cat"),
        Sort:                 models.ToPointer(models.SortEnum_POPULAR),
    }

}
```

