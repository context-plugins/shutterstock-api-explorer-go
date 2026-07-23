
# Span Type Enum

Type of span; metered spans represent a pariod of time with music, and unmetered spans denote the end of the prior metered span

## Enumeration

`SpanTypeEnum`

## Fields

| Name |
|  --- |
| `METERED` |
| `UNMETERED` |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    spanType := models.SpanTypeEnum_METERED

}
```

