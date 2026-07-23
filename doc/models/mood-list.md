
# Mood List

List of audio moods

## Structure

`MoodList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Data` | `[]string` | Required | List of audio moods |

## Example

```go
package main

import (
    "shutterstockapiexplorer/models"
)

func main() {
    moodList := models.MoodList{
        Data: []string{
            "Action / Sports",
            "Adventure / Discovery",
            "Aerobics / Workout",
            "Aggressive",
        },
    }

}
```

