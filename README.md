[web-workers-distributed-calculator](https://dirkarnez.github.io/web-workers-distributed-calculator)
====================================================================================================
Demostrating [A Tour of Go](https://go.dev/tour/concurrency/2)
```go
package main

import "fmt"

func sum(s []int, c chan int) {
	sum := 0
	for _, v := range s {
		sum += v
	}
	c <- sum // send sum to c
}

func main() {
	s := []int{1,2,3,4,5,6,7,8,9,10}

	c := make(chan int)
	go sum(s[:len(s)/2], c)
	go sum(s[len(s)/2:], c)
	x, y := <-c, <-c // receive from c

	fmt.Println(x, y, x+y)
}
```
### Tutorials
- [Concurrency in JavaScript and the power of Web Workers - DEV Community](https://dev.to/olyop/concurrency-in-javascript-and-the-power-of-web-workers-4278)
