
# Stack

Stack is a linear data structure which follows a particular order in which the operations are performed. The order may be LIFO(Last In First Out) or FILO(First In Last Out).

Mainly the following three basic operations are performed in the stack:

_**Push**_: Adds an item in the stack. If the stack is full, then it is said to be an Overflow condition.

_**Pop**_: Removes an item from the stack. The items are popped in the reversed order in which they are pushed. If the stack is empty, then it is said to be an Underflow condition.

_**Peek**_ or _**Top**_: Returns top element of stack.

_**isEmpty**_: Returns true if stack is empty, else false.

----

__Time Complexities of operations on stack:__

push(), pop(), isEmpty() and peek() all take **O(1)** time. We do not run any loop in any of these operations.

----

**Applications of stack:**

1. Balancing of symbols
2. Infix to Postfix /Prefix conversion
3. Redo-undo features at many places like editors, photoshop.
4. Forward and backward feature in web browsers
5. Used in many algorithms like Tower of Hanoi, tree traversals, stock span problem, histogram problem.
6. Other applications can be Backtracking, Knight tour problem, rat in a maze, N queen problem and sudoku solver
7. In Graph Algorithms like Topological Sorting and Strongly Connected Components

---


```go
import (
    "fmt"
)
```


```go
type Stack struct{
    elems []interface{}
}
```


```go
func (s *Stack) IsEmpty() bool {
    return (len(s.elems) == 0)
}
```


```go
func (s *Stack) Push(elem interface{}) {
    s.elems = append(s.elems, elem)
    fmt.Println("Inserted")
}
```


```go
func (s *Stack) Pop() interface{}{
    if len(s.elems) == 0{
        fmt.Println("Stack is empty")
        return nil
    }
    tmp := s.elems[len(s.elems)-1]
    s.elems = s.elems[:(len(s.elems)-1)]
    return tmp
}
```


```go
func (s *Stack) Peek() interface{}{
    if len(s.elems) == 0 {
        fmt.Println("Stack is empty")
        return nil
    }
    return s.elems[len(s.elems) - 1]
}
```


```go
s := &Stack{}
```


```go
s.IsEmpty()
```




    true




```go
s.Pop()
```

    Stack is empty



```go
s.Peek()
```

    Stack is empty



```go
s.Push(2)
```

    Inserted



```go
s.Peek()
```




    2




```go
s.Push(23)
```

    Inserted



```go
s.Peek()
```




    23


