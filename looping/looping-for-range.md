# Looping for range

## Looping for range pada array

```go
package main

import "fmt"
 
func main() {
    values := [7]int{1, 3, 5, 7, 9, 11, 13}
 
    for i, val := range values {
        fmt.Printf("value[%d] = %d \n", i, val)
    }
}
```

```
value[0] = 1 
value[1] = 3 
value[2] = 5 
value[3] = 7 
value[4] = 9 
value[5] = 11
value[6] = 13
```

## Looping for range pada slice

```go
package main

import "fmt"
 
func main() {
    values := []int{1, 3, 5, 7, 9, 11, 13}
 
    for i, val := range values {
        fmt.Printf("value[%d] = %d \n", i, val)
    }
}
```

```
value[0] = 1 
value[1] = 3 
value[2] = 5
value[3] = 7
value[4] = 9
value[5] = 11
value[6] = 13
```

## Looping for range pada map

```go
package main

import "fmt"
 
func main() {
    users := map[string]interface{}{
		"member_01" : "aliana",
		"member_02" : "dawam",
		"member_03" : "yusran",
	}
 
    for key, val := range users {
        fmt.Printf("value[%s] = %s \n", key, val)
    }
}
```

```
value[member_01] = aliana 
value[member_02] = dawam 
value[member_03] = yusran
```
