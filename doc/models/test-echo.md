
# Test Echo

Text to echo in the response

## Structure

`TestEcho`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Text` | `*string` | Optional | - |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    testEcho := models.TestEcho{
        Text:                 models.ToPointer("Test string"),
    }

}
```

