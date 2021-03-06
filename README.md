# Go Cheat Sheet (in progress ...)


For shorter code samples I skip package declaration and imports

<!-- code -->
```go
package main

import "fmt"
```

## How to install go

For installing go see here:
https://gist.github.com/vsouza/77e6b20520d07652ed7d

## Basic Stuff

- GO-Applications starts always in the package `main`
- export package elements by capital letter at the beginning

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

### Structs

```go
type person struct {
    name string
    age  int
}

person{"Markus", 33}                       // create a struct
p := person{name: "Jannik", age: 11}       // create a struct  
a := p.age                                 // access a structs parameter
```

### Collections (Array, Slice & Map)
#### Arrays

- arrays have a fixed size
```go
a := [3]int{2, 3, 4}  // init a array of 3 elements of type int
b := [...]int{2, 3}  // compiler counts the number of elements
s[3] = 100            // assign the 3rd element of myArray with 100
len(a)                // length of my array
var c = [2][2]int     // init a 2D array
```

#### Slice

- slices have a dynamic size
- slices are a reference to an array, so it describes a section of an array

```go
s := []int{1, 2, 3}
s = s[1:]           // ==>  [2,3]
var t []int
t = make([]int, 5, 5)     // make takes a type, the length and an optional capacity
                          // returns a pointer to an array
```

- the length of a slice is the number of elements it contains
- the capacity is the number of elements in the underlying array

```go
s := []int{1, 2}
s = append(s, 2, 3) // adds elements to the slice ==> [1,2,3,4]
```

#### Maps

```go
  m := make(map[string]int)             // empty empty with [key-value]val-type
  n := map[string]int{"a": 1, "b": 2}   // declare and init a map
  v1 := m["k1"]                         // get the value for a key
  delete(m, "k2")                       // removes entry from map
  _, in := m["k2"]                     // first parameter is ignored by "blank identifier"
                                        // `in` returns `boolean` if m contains the key "k2"
```

### Pointers

- The type `*T` is a pointer to a `T` value. Its zero value is `nil`.
```go
  i, j := 10, 9

  // dereferencing
  p := &i         // point to i
  fmt.Println(*p) // ==> 10

  // indirecting
  *p = 21         // set i through the pointer
  fmt.Println(i)  // ==> 21

  // modify a pointers value
  p = &j         // point to j
  *p = *p / 3    // divide j through the pointer
  fmt.Println(j) //  ==> 3
```

## Control Structures
### `if`-Statement
```go
if a := 3, b == true {   // variable a is available in all branches
    // do something
} else if c == false{
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
for i := 0; i < 10; i++ { // the init and post statement are optional
}
```
```go
var s = []int{1, 2, 4,}
for i, v := range s {   // similar to foreach-loop; i is the index and v the value
}
```

## Functions
### Basics
```go
func foo(x, y int) int {
  return x + y
}

a := foo(2,3)             //==> 5
```
```go
func foo() (int, int) {
  return 2, 3
}

a, b  := foo()             //==> 2, 3
```
### Variadic functions
- can be called with any number of trailing arguments
```go
func foo(nums ...int) {
    sums := 0
    for _, num := range nums {
        total += num
    }
}
```

### Closures
```go
func iter() func() int {
  i:=0
  return func() int {     // anonymous function
    i += 1
    return i
  }
}

it := iter()
fmt.Println(it())                  // ==> 1  
fmt.Println(it())                  // ==> 2
```

### Function as parameter or return
### Pointers and functions

## Methods & interfaces

### Basics

- a method is a function with a special receiver argument.

```go
type Vertex struct {
	X, Y float64
}

func (v Vertex) Abs() float64 {         // receiver here is `Vertex` v
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func (v *Vertex) Scale(f float64) {    // pointer receiver '*Vertex'
	v.X = v.X * f
	v.Y = v.Y * f
}

func main() {
	v := Vertex{3, 4}
  v.scale(10)
	fmt.Println(v.abs())                 // how to use a method ==> 50
}
```
### interfaces

```go
    type Geometry interface {           // basic interface
        abs() float64
    }

    type Vertex struct {      
    	X, Y float64
    }

    func (v Vertex) Abs() float64 {       // to implement an interface implement all the methods
    	return math.Sqrt(v.X*v.X + v.Y*v.Y)
    }
    func measure(g geometry) {            // generic method
        fmt.Println(g)
        fmt.Println(g.area())
        fmt.Println(g.perim())
    }

    func main() {
        v := Vertex{1, height: 2}

        measure(v)
    }
```
## Concurrency
### GOroutines

- a goroutine is a lightweight thread managed by the Go runtime.
-  goroutines run in the same address space, so you have to care about shared memory to be 'synchronized'

```go
func f(n int) {
  for i := 0; i < 10; i++ {
    fmt.Println(n, ":", i)
  }
}

func main() {
  go f(0)               // goroutine we return immediately to the next line
  var input string      // and dont wait for the function to complete
  fmt.Scanln(&input)   //  Ensures that all the numbers are printed
}
```

## References

- https://gist.github.com/vsouza/77e6b20520d07652ed7d
- https://tour.golang.org/
- https://gobyexample.com
