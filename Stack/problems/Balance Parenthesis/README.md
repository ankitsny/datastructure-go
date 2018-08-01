
# Balanced Parentheses Check

---

> Time Complexity _**O(n)**_


```go
import (
    "fmt"
    "strings"
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


```


```go
const start = "[{("
const end = ")]}"
```


```go
func validatePair(p1, p2 string) bool{
    switch(p2){
        case ")":
            return p1 == "(" 
        case "}":
             return p1 == "{"
        case "]":
            return p1 == "["
        default:
            return false
    }
}
```


```go
func isBalancedParenthesis(str string) bool{
    s := &Stack{}
    
    // Length should be even
    if len(str) & 1 == 1{
        // fmt.Println("Length Should be even")
        return false
    }
    
    // balanced pair can not start from closing parenths
    if  !strings.Contains(start, string(str[0])){
        return false
    }
    
    // balanced pair can not end from starting parents
    if !strings.Contains(end, string(str[len(str)-1])){
        return false
    }

    for _, val := range str{
        if strings.Contains(start, string(val)){
            // encountered start 
            s.Push(string(val))
        }else{
            // Encountered end
            
            if s.IsEmpty(){
                // encountered end but stack is empty
                return false
            }
            last := s.Pop()
            // Check for the valid pairs.() valid pair, {) invalid pair
            if !validatePair(last.(string), string(val)){
                return false
            }
        }
    }
    return s.IsEmpty()
}
```


```go
isBalancedParenthesis("[](()){()}")
```




    true




```go
isBalancedParenthesis("[{())()}]")
```




    false


