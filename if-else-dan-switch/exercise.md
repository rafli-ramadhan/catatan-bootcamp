# Exercise

1. Determine student grades.
2. Calculating the price with the process of input, quantity and discount.
3. Compute the vowel alphabet from a string.
4. Calculate the factorial.
5. Check the odd or even number of the input string.

```go
package main

import (
	"fmt"
	"strings"
)

// soal no 1
func SwitchExercise2(score int) {
	var result string
	switch {
	case score >= 90 :
        	result = "A"
 	case score >= 80 && score < 89 :
        	result = "B"
	case score >= 70 && score < 79 :
        	result = "C"
    	case score >= 60 && score < 69 :
        	result = "D"
	default :
		result = "E"
	}
	
	fmt.Printf("Anda mendapatkan nilai %v \n", result)
}

// soal no 2
func CalculateTotal(price float64, qty float64, discount bool) {
	var total float64 = price * qty
	if discount {
		total = total * 0.9
	}
	fmt.Printf("\nTotal : %v \n", total)
}

// soal no 3
func CalculateVocalAlphabet(input string) {
	vocals := []string{"a" ,"e" ,"i" , "o", "u"}
	var totalVocal int = 0

	for i := range input {
		for j := range vocals {
			if strings.ToLower(string(input[i])) == vocals[j] {
				totalVocal++
			}
		}
	}
	
	fmt.Printf("Total huruf vokal pada string '%v' ada %d huruf vokal.\n", input, totalVocal)
}

// soal no 4
func CalculateFactorial(input float64) {
	var result float64 = input
	for i := 1; i < int(input); i++ {
		result = result * (input - float64(i))
	}

	fmt.Printf("Hasil dari faktorial %f adalah %f \n", input, result)
}

// soal no 5
func CheckOddOrEven(input string) {
	var number int
	switch {
	case input == "satu":
		number = 1
	case input == "dua":
		number = 2
	case input == "tiga":
	    number = 3
	case input == "empat":
	    number = 4
	case input == "lima":
	    number = 5
	case input == "enam":
	    number = 6
	case input == "tujuh":
	    number = 7
	case input == "delapan":
	    number = 8
	case input == "sembilan":
	    number = 9
	case input == "sepuluh":
	    number = 10
	default:
	    fmt.Println("angka yang kamu input salah")
	}

	if number % 2 == 0 {
		fmt.Printf("\nBilangan %v adalah bilangan genap", input)
	} else {
		fmt.Printf("\nBilangan %v adalah bilangan ganjil", input)
	}
}
```
