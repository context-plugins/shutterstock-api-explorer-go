
# ISO Country Code

A valid ISO 3166-1 Alpha-2 or ISO 3166-1 Alpha-3 code.

## Class Name

`ISOCountryCode`

## Cases

| Type | Factory Method |
|  --- | --- |
| [`models.ISOCountryCodeEnum`](../../../doc/models/containers/iso-country-code.md) | models.ISOCountryCodeContainer.FromISOCountryCode(models.ISOCountryCodeEnum iSOCountryCode) |
| [`models.ISOCountryCode1Enum`](../../../doc/models/iso-country-code-1-enum.md) | models.ISOCountryCodeContainer.FromISOCountryCode1(models.ISOCountryCode1Enum iSOCountryCode1) |

## models.ISOCountryCodeEnum

### Initialization Code

#### Example

```go
value := models.ISOCountryCodeContainer.FromISOCountryCode(models.ISOCountryCodeEnum_ABW)
```

## models.ISOCountryCode1Enum

### Initialization Code

#### Example

```go
value := models.ISOCountryCodeContainer.FromISOCountryCode1(models.ISOCountryCode1Enum_AF)
```

