
# Instrument List

List of instruments

## Structure

`InstrumentList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | `[]string` | Required | List of instruments |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    instrumentList := models.InstrumentList{
        Data: []string{
            "Orchestra",
            "Organ",
            "Oud",
            "Pads",
            "Electric Guitar",
        },
    }

}
```

