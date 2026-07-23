
# Contributor Profile

Contributor profile data

## Structure

`ContributorProfile`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `About` | `*string` | Optional | Short description of the contributors' library |
| `ContributorType` | `[]string` | Optional | Type of content that the contributor specializes in (photographer, illustrator, etc) |
| `DisplayName` | `*string` | Optional | Preferred name to be displayed for the contributor |
| `Equipment` | `[]string` | Optional | List of equipment used by the contributor (Canon EOS 5D Mark II, etc) |
| `Id` | `string` | Required | Contributor ID |
| `Location` | `*string` | Optional | Country code representing the contributor's locale |
| `PortfolioUrl` | `*string` | Optional | Web URL for the contributors' profile |
| `SocialMedia` | [`*models.ContributorProfileSocialMedia`](../../doc/models/contributor-profile-social-media.md) | Optional | Contributor profile social media links |
| `Styles` | `[]string` | Optional | List of styles that the contributor specializes in (lifestyle, mixed media, etc) |
| `Subjects` | `[]string` | Optional | Generic list of subjects for contributors' work (food_and_drink, holiday, people, etc) |
| `Website` | `*string` | Optional | Personal website for the contributor |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    contributorProfile := models.ContributorProfile{
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
    }

}
```

