
# Access Token Details

Access token details that are currently associated with this user

## Structure

`AccessTokenDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ClientId` | `*string` | Optional | Client ID that is associated with the user |
| `ContributorId` | `*string` | Optional | Contributor ID that is associated with the user |
| `CustomerId` | `*string` | Optional | Customer ID that is associated with the user |
| `ExpiresIn` | `*int` | Optional | Number of seconds until the access token expires; no expiration if this value is null |
| `OrganizationId` | `*string` | Optional | Organization ID that is associated with the user |
| `Realm` | [`*models.RealmEnum`](../../doc/models/realm-enum.md) | Optional | Type of access token |
| `Scopes` | `[]string` | Optional | Scopes that this access token provides when used as authentication |
| `UserId` | `*string` | Optional | User ID that is associated with the user |
| `Username` | `*string` | Optional | User name that is associated with the user |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    accessTokenDetails := models.AccessTokenDetails{
        ClientId:             models.ToPointer("c456b-26230-fa8ed-d19ab-05ce2-bf0aa"),
        ContributorId:        models.ToPointer("contributor_id8"),
        CustomerId:           models.ToPointer("123456789"),
        ExpiresIn:            models.ToPointer(3600),
        OrganizationId:       models.ToPointer("organization_id2"),
        Realm:                models.ToPointer(models.RealmEnum_CUSTOMER),
        Scopes:               []string{
            "collections.edit",
            "collections.view",
            "licenses.create",
            "licenses.view",
            "purchases.view",
            "user.view",
        },
        UserId:               models.ToPointer("123456789"),
        Username:             models.ToPointer("jdoe"),
    }

}
```

