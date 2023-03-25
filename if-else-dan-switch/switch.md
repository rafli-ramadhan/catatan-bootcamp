# Switch

## Switch with Single Case

```go
package main

import (
    "fmt"
)

func choose(value int) {
	switch(value) {
	case 1:
		fmt.Println(1)
	case 2:
		fmt.Println(2)
	case 3:
		fmt.Println(3)
	}
}

func main() {
	choose(1)
	choose(2)
}
```



## Switch Case with fallthrough

```go
package main
import "fmt"

func main() {
  dayOfWeek := 5

  switch dayOfWeek {
    case 1:
      fmt.Println("Sunday")
      fallthrough
    case 2:
      fmt.Println("Monday")
      fallthrough
    case 3:
      fmt.Println("Tuesday")
      fallthrough
    case 4:
      fmt.Println("Wednesday")
      fallthrough
    case 5:
      fmt.Println("Thursday")
      fallthrough
    case 6:
      fmt.Println("Friday")
      fallthrough
    case 7:
      fmt.Println("Saturday")
      fallthrough
    default:
      fmt.Println("Invalid day")
      // fallthrough // -> cannot fallthrough final case in switch
  }
}
```

```
Thursday
Friday
Saturday
Invalid day
```

## Switch with Multiple Case

```go
package main
import "fmt"

func main() {
    day := "Monday"
    
    switch day {
        case "Monday", "Tuesday", "Wednesday", "Thursday", "Friday":
        fmt.Println("Work Day")
        case "Saturday", "Sunday":
        fmt.Println("Weekend")
    }
}
```

```
Work Day
```

