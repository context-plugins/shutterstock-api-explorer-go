
# Key

The key signature active at the beginning of the region

## Structure

`Key`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `TonicAccidental` | [`*models.TonicAccidentalEnum`](../../doc/models/tonic-accidental-enum.md) | Optional | A text representation of the accidental; if this field is specified, the tonic_note field should also be specified |
| `TonicNote` | [`*models.TonicNoteEnum`](../../doc/models/tonic-note-enum.md) | Optional | A text representation of the musical note; if this field is specified, the tonic_accidental field should also be specified |
| `TonicQuality` | [`*models.TonicQualityEnum`](../../doc/models/tonic-quality-enum.md) | Optional | The scale quality; if this field is not specified, the API selects the quality automatically |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    key := models.Key{
        TonicAccidental:      models.ToPointer(models.TonicAccidentalEnum_FLAT),
        TonicNote:            models.ToPointer(models.TonicNoteEnum_C),
        TonicQuality:         models.ToPointer(models.TonicQualityEnum_MAJOR),
    }

}
```

