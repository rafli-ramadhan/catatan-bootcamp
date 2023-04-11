# Unit Testing in Go

main.go

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	result := SayHi("Utsman")
	fmt.Println(result)
}

func SayHi(name string) string {
	return "Hello " + name
}

func Greeting(name string) string {
	if name == "Andi" {
		return "Hai Andi"
	} else {
		return "You are not Andi"
	}
}
```

main\_test.go

```go
package main

import (
	"testing"
)

func TestSayHi(t *testing.T) {
	t.Log("Start test")
	type args struct {
		name string
	}
	tests := []struct {
		name string
		args args
		want string
	}{
		{
			name: "Say hi unit test",
			args: args{name: "Andi"},
			want: "Hello Andi",
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

func TestGreeting(t *testing.T) {
	type args struct {
		name string
	}
	tests := []struct {
		name string
		args args
		want string
	}{
		{
			name: "Greeting unit test",
			args: args{"Andi"},
			want: "Hai Andi",
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			if got := Greeting(tt.args.name); got != tt.want {
				t.Errorf("Greeting() = %v, want %v", got, tt.want)
			}
		})
	}
}
```

```
PS D:\bootcamp-go\go-unit-test> go test
--- FAIL: TestGreeting (0.00s)
    --- FAIL: TestGreeting/Greeting_unit_test (0.00s)
        main_test.go:50: Greeting() = Hello Andi, want Hai Andi
FAIL
exit status 1
FAIL    unit-testing    1.029s
PS D:\bootcamp-go\go-unit-test> go test
PASS
ok      unit-testing    0.503s
```
