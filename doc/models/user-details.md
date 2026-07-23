
# User Details

User details

## Structure

`UserDetails`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ContributorId` | `*string` | Optional | Unique internal identifier of the user, as a contributor |
| `CustomerId` | `*string` | Optional | Unique internal identifier of the user, as a purchaser |
| `Email` | `*string` | Optional | Email address of the user |
| `FirstName` | `*string` | Optional | First name of the user |
| `FullName` | `*string` | Optional | Full name including first, middle, and last name of the user |
| `Id` | `*string` | Optional | Unique internal identifier for the user, not tied to contributor or purchasing customer |
| `IsPremier` | `*bool` | Optional | True if the user has access to the Premier collection, false otherwise |
| `IsPremierParent` | `*bool` | Optional | True if the user has access to the Premier collection and also has child users |
| `Language` | `*string` | Optional | Main language of the user account |
| `LastName` | `*string` | Optional | Last name of the user |
| `OnlyEnhancedLicense` | `*bool` | Optional | True if the user has an enterprise license, false otherwise |
| `OnlySensitiveUse` | `*bool` | Optional | True if the user has access to sensitive use only, false otherwise |
| `OrganizationId` | `*string` | Optional | Unique internal identifier for the user's organization, specific to Premier users |
| `PremierPermissions` | `[]string` | Optional | List of permissions allowed through the Premier client |
| `Username` | `*string` | Optional | User name associated to the user |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    userDetails := models.UserDetails{
        ContributorId:        models.ToPointer("212"),
        CustomerId:           models.ToPointer("customer_id2"),
        Email:                models.ToPointer("email2"),
        FirstName:            models.ToPointer("John"),
        FullName:             models.ToPointer("John Doe"),
        Id:                   models.ToPointer("101782699"),
        Language:             models.ToPointer("es"),
        LastName:             models.ToPointer("Doe"),
        Username:             models.ToPointer("jdoe"),
    }

}
```

