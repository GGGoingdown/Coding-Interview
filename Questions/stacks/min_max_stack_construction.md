# Min Max stack construction

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
### Solution 1
```go
import (
	"fmt"
	"math"
)
// O(n) pop, iterate all data and update mininum and maxnum number
// O(1) push
// O(1) space
type MinMaxStack struct {
	data []int
	min  float64
	max  float64
}

func NewMinMaxStack() *MinMaxStack {
	return &MinMaxStack{
		data: make([]int, 0),
		min:  math.Inf(1),
		max:  math.Inf(-1),
	}
}

func (stack *MinMaxStack) Peek() int {
	if len(stack.data) == 0 {
		return -1
	}
	return stack.data[len(stack.data)-1]
}

func (stack *MinMaxStack) Pop() int {
	if len(stack.data) == 0 {
		return -1
	}

	val := stack.data[len(stack.data)-1]
	stack.data = stack.data[:len(stack.data)-1]
	stack.UpdateMinAndMax()
	return val
}

func (stack *MinMaxStack) UpdateMinAndMax() {
	min := math.Inf(1)
	max := math.Inf(-1)
	for _, val := range stack.data {
		if float64(val) > max {
			max = float64(val)
		}
		if float64(val) < min {
			min = float64(val)
		}
	}
	stack.max = max
	stack.min = min
}

func (stack *MinMaxStack) Push(number int) {
	stack.data = append(stack.data, number)
	if float64(number) > stack.max {
		stack.max = float64(number)
	}
	if float64(number) < stack.min {
		stack.min = float64(number)
	}
}

func (stack *MinMaxStack) GetMin() int {
	return int(stack.min)
}

func (stack *MinMaxStack) GetMax() int {
	return int(stack.max)
}

```

### Solution 2
```go
// O(1) time | O(1) space
type MinMaxStack struct {
	data []int
	min  []int
	max  []int
}

func NewMinMaxStack() *MinMaxStack {
	return &MinMaxStack{
		data: make([]int, 0),
		min:  make([]int, 0),
		max:  make([]int, 0),
	}
}

func (stack *MinMaxStack) Peek() int {
	if len(stack.data) == 0 {
		return -1
	}
	return stack.data[len(stack.data)-1]
}

func (stack *MinMaxStack) Pop() int {
	if len(stack.data) == 0 {
		return -1
	}

	val := stack.data[len(stack.data)-1]
	stack.data = stack.data[:len(stack.data)-1]
	stack.min = stack.min[:len(stack.min)-1]
	stack.max = stack.max[:len(stack.max)-1]
	return val
}

func (stack *MinMaxStack) Push(number int) {
	if len(stack.data) == 0 {
		stack.min = append(stack.min, number)
		stack.max = append(stack.max, number)
	} else {
		min := stack.min[len(stack.min)-1]
		if number < min {
			min = number
		}
		stack.min = append(stack.min, min)

		max := stack.max[len(stack.max)-1]
		if number > max {
			max = number
		}
		stack.max = append(stack.max, max)
	}

	stack.data = append(stack.data, number)
}

func (stack *MinMaxStack) GetMin() int {
	if len(stack.data) <= 0 {
		return -1
	}
	return stack.min[len(stack.min)-1]
}

func (stack *MinMaxStack) GetMax() int {
	if len(stack.data) <= 0 {
		return -1
	}
	return stack.max[len(stack.max)-1]
}

```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/min-max-stack-construction)