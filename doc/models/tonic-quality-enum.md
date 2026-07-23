
# Tonic Quality Enum

The scale quality; if this field is not specified, the API selects the quality automatically

## Enumeration

`TonicQualityEnum`

## Fields

| Name |
|  --- |
| `MAJOR` |
| `NATURALMINOR` |
| `HARMONICMINOR` |
| `MELODICMINOR` |
| `IONIAN` |
| `DORIAN` |
| `PHRYGIAN` |
| `LYDIAN` |
| `MIXOLYDIAN` |
| `AEOLIAN` |
| `LOCRIAN` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    tonicQuality := models.TonicQualityEnum_DORIAN

}
```

