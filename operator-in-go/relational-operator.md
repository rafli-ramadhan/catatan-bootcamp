# Relational Operator

Relational operator -> == && !=

```go
package main

import (
	"fmt"
)

func main() {
	var name1 = "Test1"
	var name2 = "Test2"

	var compareName1 bool = name1 == name2
	fmt.Println(compareName1)

	var name3 = "Test1"
	var name4 = "test1"

	var compareName2 bool = name3 == name4
	fmt.Println(compareName2)

	var value1 = 123
	var value2 = 121

	var compareDigit1 bool = value1 != value2
	fmt.Println(compareDigit1)

	// var value3 = 2
	// var value4 = 2.0

	// var compareDigit2 bool = value3 == value4 // -> cannot compare value3 == value4 (mismatched types int and float64)
	// fmt.Println(compareDigit2)

	var float1 = 123
	var float2 = 121

	var compareFloat1 bool = float1 == float2
	fmt.Println(compareFloat1)

	var float3 = 123.0
	var float4 = 123.00

	var compareFloat2 bool = float3 == float4
	fmt.Println(compareFloat2)
}
```

```
false
false
true
false
true
```
