
# Implement Queu


```go
import(
    "fmt"
)
```


```go
// Stack
type Stack struct{
    elems []interface{}
}

func (s *Stack) IsEmpty() bool {
    return (len(s.elems) == 0)
}

func (s *Stack) Push(elem interface{}) {
    s.elems = append(s.elems, elem)
    // fmt.Println("Inserted")
}

func (s *Stack) Pop() interface{}{
    if len(s.elems) == 0{
        // fmt.Println("Stack is empty")
        return nil
    }
    tmp := s.elems[len(s.elems)-1]
    s.elems = s.elems[:(len(s.elems)-1)]
    return tmp
}

func (s *Stack) Peek() interface{}{
    if len(s.elems) == 0 {
        // fmt.Println("Stack is empty")
        return nil
    }
    return s.elems[len(s.elems) - 1]
}

func (s *Stack) Size()int{
    return len(s.elems)
}
```


```go
// Queue
type Queue struct{
    InStack *Stack
    OutStack *Stack
}

func (q *Queue) Enqueue(val interface{}){
    if q.InStack == nil{
        q.InStack = &Stack{}
    }
    q.InStack.Push(val)
}

func (q *Queue) Dequeue() interface{}{
    if q.OutStack == nil{
        q.OutStack = &Stack{}
    }
    if q.OutStack.Size() == 0{
        for q.InStack.Size() != 0{
            q.OutStack.Push(q.InStack.Pop())
        }
    }
    return q.OutStack.Pop()
}
```


```go
q := &Queue{}
```


```go
q.Enqueue(1)
```


```go
q.Enqueue(2)
```


```go
q.Dequeue()
```




    1




```go
q.Dequeue()

```




    2




```go
q.Enqueue(22)

```


```go
q.Enqueue(33)
```


```go
q.Dequeue()
```




    22




```go
q.Enqueue(44)
```


```go
q.Dequeue()
```




    33


