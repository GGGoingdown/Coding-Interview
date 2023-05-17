# Bubble Sort

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
func BubbleSort(array []int) []int {
	if len(array) <= 1 {
		return array
	}

	for i := len(array) - 1; i > 0; i-- {
		for j := 0; j < i; j++ {
			if array[j] > array[j+1] {
				array[j+1], array[j] = array[j], array[j+1]
			}
		}
	}

	return array
}

```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/bubble-sort)