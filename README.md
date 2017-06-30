# Go Cheat Sheet


For shorter code samples I skip package declaration and imports

<!-- code -->
```go
package main

import "fmt"
```

## How to install go



## Basic Stuff

- GO-Applications starts always in the package `main`
- export package elements by capital letter at the beginning
- var and init

## Variables and constants

- variables can be declared on package or method level

```go
var a,b int = 3,6 // initializing of multiple variables
c := "short"      // shorthand declaration and initializing (typed by its value)
const foo = "ab"  // a constant
```

## Data types
### Basic data types
- `bool`
- `string`
- `int`	  `int8`  `int16`		 `int32`	  `int64`
- `uint`	`uint8`	`uinit16`	 `unint32` 	`uint64` 	`uintptr`
- `byte` (= `uint8`)
- `rune` (= `int32`)
- `float32` `float64`
- `complex64` `complex128`

### Collections (Array, Slice & Map)

- arrays have a fixed size
```go
myArray := [3]int{2, 3, 4}  // init a array of 3 elements of type int
myArray2 := [...]int{2, 3}  // compiler counts the number of elements
myArray[3] = 100            // assign the 3rd element of myArray with 100
len(myArray)                // length of my array
var myArray = [2][2]int     // init a 2D array
```

- slices have a dynamic size
- slices are a reference to an array, so it describes a section of an array
```go
mySlice := []int{1, 2, 3}
mySlice = s[1:]           // ==>  [2,3]
var s []int
s = make([]int, 5, 5)     // make takes a type, the length and an optional capacity
                          // returns a pointer to an array
```
- the length of a slice is the number of elements it contains
- the capacity is the number of elements in the underlying array

```go
mySlice := []int{1, 2}
mySlice = append(mySlice, 2, 3) // adds elements to the slice ==> [1,2,3,4]
```


### Pointers

## Control Structures
### `if`-Statement
```go
if a := 3, foo2 == true {   // variable a is available in all branches
    // do something
} else if foo3 == false{
    // do something
} else {
  // do something
}
```
- the ternary operator is not available in GO

### `switch`-Statement

```go
switch time.Now().Weekday() {
 case time.Saturday, time.Sunday:
      // do something
 default:
     // do something
 }
```
- you can use switch statements for types and values

### `for`-loop
```go
sum := 0
for i := 0; i < 10; i++ { // the init and post statement are optional
  sum += i
}
```
```go
var s = []int{1, 2, 4,}

for i, v := range s {   // similar to foreach-loop; i is the index and v the value
}
```

## Functions

## Methods & Structs


## Topic I



## Topic II



## Topic III
