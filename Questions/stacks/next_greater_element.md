# Next Greater Element

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
// O(n) time | O(n) space, n is the size of input array
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

func NextGreaterElement(array []int) []int {
	stack := new(Stack)
	result := make([]int, len(array))
	for i := 0; i < len(result); i++ {
		result[i] = -1
	}

	for i := 0; i < len(array)*2; i++ {
		j := i % len(array)
		for stack.length > 0 {
			curVal := array[j]
			idx, err := stack.Peek()
			if err != nil {
				panic(err.Error())
			}
			if curVal > array[idx] {
				result[idx] = curVal
				_, err = stack.Pop()
				if err != nil {
					panic(err.Error())
				}
			} else {
				break
			}
		}
		stack.Append(j)
	}

	return result
}

```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/next-greater-element)