# lqueue
This is a generalized queue package with clean and transparent API for the Go language.

## Features
- Lightweight and Fast.
- Native Go implementation.
- Support all data types.

## Requirements
- Go 1.9 or higher. We aim to support the 3 latest versions of Go.

## Installation
Simple install the package to your [$GOPATH](https://github.com/golang/go/wiki/GOPATH "GOPATH") with the [go tool](https://golang.org/cmd/go/ "go command") from shell:
```bash
$ go get -u github.com/lovesaroha/lqueue
```
Make sure [Git is installed](https://git-scm.com/downloads) on your machine and in your system's `PATH`.

## Usage

### Create Queue

```Golang
  // Create a queue (0 for normal queue).
  queue = lqueue.Create(0)

  // Add values in queue.
  queue.Enqueue(2)
  queue.Enqueue(3)
  queue.Enqueue(4)

  // Remove value from queue and return value.
  queue.Dequeue()

  // Print values in queue.
  queue.Print()

```

### Create Min Priority Queue

```Golang
  // Create a queue (1 for ascending order).
  queue = lqueue.Create(1)

  // Add values in queue.
  queue.Enqueue(4)
  queue.Enqueue(2)
  queue.Enqueue(1)

  // Remove value from queue and return value (1).
  queue.Dequeue()

  // Print values in queue.
  queue.Print()

```

### Create Max Priority Queue

```Golang
  // Create a queue (-1 for descending order).
  queue = lqueue.Create(-1)

  // Add values in queue.
  queue.Enqueue("love")
  queue.Enqueue("saroha")
  queue.Enqueue("git")

  // Remove value from queue and return value ("saroha").
  queue.Dequeue()

  // Print values in queue.
  queue.Print()

```

### Add Multiple Values

```Golang
  // Create a queue (0 for normal queue).
  queue = lqueue.Create(0)

  // Add values in queue.
  queue.EnqueueValues([]interface{}{1,2,3,4,5,6,7,8,9})

  // Remove value from queue and return value.
  queue.Dequeue()

  // Print values in queue.
  queue.Print()
```

### Custom Data Type
```Golang 
  type user struct {
    name string
  }

  // Create a queue (0 for normal queue).
  queue = lqueue.Create(0)

  // Add values in queue.
  queue.Enqueue(user{name: "love"})
  queue.Enqueue(user{name: "joe"})
  queue.Enqueue(user{name: "doe"})

  // Remove value from queue and return value.
  queue.Dequeue()

  // Print values in queue.
  queue.Print()

```
### Priority Queue With Custom Data Type
```Golang 
  type user struct {
    name string
    age int
  }

  // Compare function for custom data type.
  func compare(a interface{} , b interface{}) bool {
    // For min priority queue.
    return a.(int) <= b.(int) 
  }

  // Create a queue (0 for normal queue).
  queue = lqueue.Create(0)

  // Add values in queue with given condition.
  queue.EnqueueWith(user{name: "love" , age: 27} , compare)
  queue.EnqueueWith(user{name: "joe" , age: 30} , compare)
  queue.EnqueueWith(user{name: "doe" , age: 34} , compare)

  // Remove value from queue and return value.
  queue.Dequeue()

  // Print values in queue.
  queue.Print()

```

### Remove Values With Specific Data Type
```Golang 

  // Create a queue (0 for normal queue).
  queue = lqueue.Create(0)

  // Add values in queue.
  queue.Enqueue(2)
  queue.Enqueue(4)
  queue.Enqueue(6)
  queue.Enqueue("love")

  // Remove value from queue and return int value (2).
  queue.DequeueInt()
  // Remove value from queue and return float64 value (4.00).
  queue.DequeueFloat64()
  // Remove value from queue and return string value ("6").
  queue.DequeueString()

  // Print values in queue.
  queue.Print()
```  
