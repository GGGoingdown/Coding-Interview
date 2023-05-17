# Sort Stack

### Description:  


**Sample input:**  
```

```

**Sample output:**  
```
```


---
### Think :

---
### Solution
```go
package main

import (
	"errors"
	"fmt"
)

type Stack struct {
	array  []int
	length int
}

func (s *Stack) Peek() (int, error) {
	if len(s.array) == 0 {
		return 0, errors.New("empty stack")
	}
	return s.array[len(s.array)-1], nil
}

func (s *Stack) Append(val int) {
	s.array = append(s.array, val)
	s.length++
}

func (s *Stack) Pop() (int, error) {
	if len(s.array) == 0 {
		return 0, errors.New("empty stack")
	}

	val := s.array[len(s.array)-1]
	s.array = s.array[:len(s.array)-1]
	s.length--
	return val, nil
}

func SortStack(stack []int) []int {
	if len(stack) == 0 {
		return []int{}
	}

	s := new(Stack)
	for _, val := range stack {
		s.Append(val)
	}

	sort(s)
	return s.array
}

func sort(s *Stack) {
	if s.length <= 0 {
		return
	}
	val, err := s.Pop()
	if err != nil {
		panic(err.Error())
	}
	sort(s)
	insertSorted(s, val)
}

func insertSorted(s *Stack, val int) {
	if s.length <= 0 {
		s.Append(val)
		return
	}

	bigVal, err := s.Peek()
	if err != nil {
		panic(err.Error())
	}

	if val > bigVal {
		s.Append(val)
		return
	}

	bigVal, err = s.Pop()
	if err != nil {
		panic(err.Error())
	}
	insertSorted(s, val)
	s.Append(bigVal)
}
```


---

### Link:
- [ALgoExpert](https://www.algoexpert.io/questions/sort-stack)