# Switch

## Switch with Single Case

Catatan : value dalam switch bisa diberi tanda (...) atau bisa juga tidak diberi tanda (...).

```go
package main

import (
    "fmt"
)

func choose(value int) {
	switch value {
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

```
1
2
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

## Switch without Expression

Bisa digunakan dengan relational operator (>, <, >=, <=, ==, &&, atau !=).

```go
package main
import "fmt"

func main() {
    day := "Monday"
    
    switch {
    case day == "Monday" || day == "Tuesday" || day == "Wednesday" || day == "Thursday" || day == "Friday":
        fmt.Println("Work Day")
    case day == "Saturday" || day == "Sunday":
        fmt.Println("Weekend")
    }
}
```

```
Work Day
```

```go
package main

import "fmt"

func main() {
  var isValid bool = true

  switch {
    case isValid:
      fmt.Println("true")
     default:
      fmt.Println("false")
  }
}
```

```
true
```

```go
package main

import "fmt"

func main() {
  numOfDays := 28

  switch {
    case numOfDays == 28:
      fmt.Println("It's February")
    default:
      fmt.Println("Not February")
  }
}
```

```
It's February
```

## Go Switch Optional Statement

```go
package main

import "fmt"

func main() {
    switch  day := "Monday"; day {
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

```go
package main

import "fmt"

func main() {
  switch isValid := false; isValid {
    case isValid:
      fmt.Println("true")
     default:
      fmt.Println("false")
  }
}
```

```
true
```

```go
package main

import "fmt"

func main() {
  switch numOfDays := 28; numOfDays {
    case 28:
      fmt.Println("It's February")
    default:
      fmt.Println("Not February")
  }
}
```

```
It's February
```
