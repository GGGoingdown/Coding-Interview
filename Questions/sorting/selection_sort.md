# Selection Sort

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
// O(n^2) time | O(1) space
func SelectionSort(array []int) []int {
	if len(array) <= 1 {
		return array
	}
	for i := 0; i < len(array)-1; i++ {
		for j := i + 1; j < len(array); j++ {
			if array[j] < array[i] {
				array[i], array[j] = array[j], array[i]
			}
		}
	}
	return array
}
```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/selection-sort)