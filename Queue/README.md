
# __Queue__

A Queue is a linear structure which follows a particular order in which the operations are performed. The order is First In First Out (FIFO). A good example of a queue is any queue of consumers for a resource where the consumer that came first is served first. The difference between stacks and queues is in removing. In a stack we remove the item the most recently added; in a queue, we remove the item the least recently added.

---

## Applications of Queue Data Structure
Queue is used when things don’t have to be processed immediately, but have to be processed in First In First Out order like Breadth First Search. This property of Queue makes it also useful in following kind of scenarios.

1. When a resource is shared among multiple consumers. Examples include CPU scheduling, Disk Scheduling.

2. When data is transferred asynchronously (data not necessarily received at same rate as sent) between two processes. Examples include IO Buffers, pipes, file IO, etc.



```go
import(
    "fmt"
)
```


```go
// Queue : queue structure
type Queue struct{
    elems []interface{}
}
```


```go
// Size : this function reurns the size of queue
func (q *Queue) Size() int{
    return len(q.elems)
}
```


```go
// IsEmpty : this function bool value, if the queue is empty then returns true and vice-versa
func (q *Queue) IsEmpty() bool{
    return (len(q.elems) == 0)
}
```


```go
// Enqueue : this function inserts element
func (q *Queue) Enqueue(val interface{}) interface{}{
    q.elems = append(q.elems, val)
    fmt.Println(val, " enqueued")
}
```


```go
// Dequeue : this function pops out an element in FIFO 
func (q *Queue) Dequeue() interface{}{
    if q.IsEmpty(){
        fmt.Println("Queue is empty")
        return nil
    }
    tmp := q.elems[0]
    q.elems = q.elems[1:]
    fmt.Println(tmp, " dequeued")
}
```


```go
q := &Queue{}
```


```go
q.Size()
```




    0




```go
q.IsEmpty()
```




    true




```go
q.Enqueue(33)
```

    33  enqueued



```go
q.IsEmpty()
```




    false




```go
q.Size()
```




    1




```go
q.Enqueue(333)
```

    333  enqueued



```go
q.Size()
```




    2




```go
q.Dequeue()
```

    33  dequeued



```go
q.Dequeue()
```

    333  dequeued



```go
q.Size()
```




    0


