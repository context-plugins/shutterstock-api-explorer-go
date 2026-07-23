
# Tonic Accidental Enum

A text representation of the accidental; if this field is specified, the tonic_note field should also be specified

## Enumeration

`TonicAccidentalEnum`

## Fields

| Name |
|  --- |
| `ENUMDOUBLEFLAT` |
| `FLAT` |
| `NATURAL` |
| `SHARP` |
| `ENUMDOUBLESHARP` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    tonicAccidental := models.TonicAccidentalEnum_FLAT

}
```

