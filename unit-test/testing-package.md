# Testing Package

main.go

```go
package main

import (
	"fmt"
)

func main() {
	result := SayHi("Utsman")
	fmt.Println(result)
}

func SayHi(name string) string {
	return "Hello " + name
}
```

main\_test.go

```go
package main

import "testing"

func TestSayHi(t *testing.T) {
	type args struct {
		name string
	}
	tests := []struct {
		name string
		args args
		want string
	}{
		// TODO: Add test cases.
		{
			name: "Test-1", 			// -> test name
			args: args{name: "Andi"}, 	// -> argument
			want: "Hello Andi", 		// -> result
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			if got := SayHi(tt.args.name); got != tt.want {
				t.Errorf("SayHi() = %v, want %v", got, tt.want)
			}
		})
	}
}

```

```
PS D:\bootcamp-go\go-unit-test> go test
PASS
ok      unit-testing    0.295s
```
