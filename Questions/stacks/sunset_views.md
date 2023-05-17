# Sunset Views

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
// O(n) time | O(n) space
func SunsetViews(buildings []int, direction string) []int {
	result := make([]int, 0)
	tallest := 0
	if direction == "EAST" {
		stack := make([]int, 0)
		for i := len(buildings) - 1; i > -1; i-- {
			curHeight := buildings[i]
			if curHeight > tallest {
				stack = append(stack, i)
				tallest = curHeight
			}
		}
		for i := len(stack)-1; i > -1; i-- {
			result = append(result, stack[i])
		}

	} else {
		for i := 0; i < len(buildings); i++ {
			curHeight := buildings[i]
			if curHeight > tallest {
				result = append(result, i)
				tallest = curHeight
			}
		}

	}

	return result
}

```
---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/sunset-views)