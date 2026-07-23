
# Contributor Profile Social Media

Contributor profile social media links

## Structure

`ContributorProfileSocialMedia`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Facebook` | `*string` | Optional | Facebook link for contributor |
| `GooglePlus` | `*string` | Optional | Google+ link for contributor |
| `Linkedin` | `*string` | Optional | LinkedIn link for contributor |
| `Pinterest` | `*string` | Optional | Pinterest page for contributor |
| `Tumblr` | `*string` | Optional | Tumblr link for contributor |
| `Twitter` | `*string` | Optional | Twitter link for contributor |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    contributorProfileSocialMedia := models.ContributorProfileSocialMedia{
        Facebook:             models.ToPointer("http://example.com/jdoe"),
        GooglePlus:           models.ToPointer("http://example.com/jdoe"),
        Linkedin:             models.ToPointer("http://example.com/jdoe"),
        Pinterest:            models.ToPointer("http://example.com/jdoe"),
        Tumblr:               models.ToPointer("http://example.com/jdoe"),
        Twitter:              models.ToPointer("http://example.com/jdoe"),
    }

}
```

