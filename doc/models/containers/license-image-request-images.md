
# License Image Request Images

## Class Name

`LicenseImageRequestImages`

## Cases

| Type | Factory Method |
|  --- | --- |
| [`models.LicenseImage`](../../../doc/models/license-image.md) | models.LicenseImageRequestImagesContainer.FromLicenseImage(models.LicenseImage licenseImage) |
| [`models.LicenseImageVector`](../../../doc/models/license-image-vector.md) | models.LicenseImageRequestImagesContainer.FromLicenseImageVector(models.LicenseImageVector licenseImageVector) |

## models.LicenseImage

### Initialization Code

#### Example

```go
value := models.LicenseImageRequestImagesContainer.FromLicenseImage(models.LicenseImage{
    EditorialAcknowledgement: models.ToPointer(true),
    Format:                   models.ToPointer(models.FormatEnum_JPG),
    ImageId:                  "123456789",
    Metadata:                 models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
    Price:                    models.ToPointer(float64(12.34)),
    ShowModal:                models.ToPointer(true),
    Size:                     models.ToPointer(models.Size2Enum_SMALL),
    SubscriptionId:           models.ToPointer("s12345678"),
})
```

## models.LicenseImageVector

### Initialization Code

#### Example

```go
value := models.LicenseImageRequestImagesContainer.FromLicenseImageVector(models.LicenseImageVector{
    EditorialAcknowledgement: models.ToPointer(true),
    Format:                   models.ToPointer(models.Format1Enum_EPS),
    ImageId:                  "123456789",
    Metadata:                 models.ToPointer(interface{}("[customer_id, 12345][geo_location, US][number_viewed, 15][search_term, dog]")),
    Price:                    models.ToPointer(float64(12.34)),
    ShowModal:                models.ToPointer(true),
    Size:                     models.ToPointer(models.Size3Enum_VECTOR),
    SubscriptionId:           models.ToPointer("s12345678"),
})
```

