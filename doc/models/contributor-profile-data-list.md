
# Contributor Profile Data List

List of contributor profiles

## Structure

`ContributorProfileDataList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | [`[]models.ContributorProfile`](../../doc/models/contributor-profile.md) | Optional | Conributor profiles |
| `Errors` | [`[]models.Error`](../../doc/models/error.md) | Optional | Error list; appears only if there was an error |
| `Message` | `*string` | Optional | Error message |
| `Page` | `*int` | Optional | Page of response |
| `PerPage` | `*int` | Optional | Number of contributors per page |
| `TotalCount` | `*int` | Optional | Total count of contributors for this request |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    contributorProfileDataList := models.ContributorProfileDataList{
        Data:                 []models.ContributorProfile{
            models.ContributorProfile{
                About:                models.ToPointer("John Doe's photographs"),
                ContributorType:      []string{
                    "photographer",
                },
                DisplayName:          models.ToPointer("John Doe"),
                Equipment:            []string{
                    "Nikon",
                    "Fuji",
                },
                Id:                   "12345678",
                Location:             models.ToPointer("US"),
                PortfolioUrl:         models.ToPointer("https://www.shutterstock.com/g/jdoe"),
                SocialMedia:          models.ToPointer(models.ContributorProfileSocialMedia{
                    Facebook:             models.ToPointer("http://example.com/jdoe"),
                    GooglePlus:           models.ToPointer("http://example.com/jdoe"),
                    Linkedin:             models.ToPointer("http://example.com/jdoe"),
                    Pinterest:            models.ToPointer("http://example.com/jdoe"),
                    Tumblr:               models.ToPointer("http://example.com/jdoe"),
                    Twitter:              models.ToPointer("http://example.com/jdoe"),
                }),
                Styles:               []string{
                    "landscape",
                    "nature",
                    "footage_travel",
                },
                Subjects:             []string{
                    "animals",
                    "landmarks",
                    "nature",
                    "objects",
                    "recreation",
                },
                Website:              models.ToPointer("http://example.com/profiles/jdoe"),
            },
        },
        Errors:               []models.Error{
            models.Error{
                Code:                 models.ToPointer("code8"),
                Data:                 models.ToPointer("data0"),
                Items:                []interface{}{
                    interface{}("[key1, val1][key2, val2]"),
                },
                Message:              "message0",
                Path:                 models.ToPointer("path4"),
            },
            models.Error{
                Code:                 models.ToPointer("code8"),
                Data:                 models.ToPointer("data0"),
                Items:                []interface{}{
                    interface{}("[key1, val1][key2, val2]"),
                },
                Message:              "message0",
                Path:                 models.ToPointer("path4"),
            },
        },
        Message:              models.ToPointer("message4"),
        Page:                 models.ToPointer(1),
        PerPage:              models.ToPointer(5),
        TotalCount:           models.ToPointer(15),
    }

}
```

