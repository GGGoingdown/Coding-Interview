# Quick sort

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
# Recursive 
```go
func QuickSort(array []int) []int {
	if len(array) <= 1 {
		return array
	}
	quickSortHelper(array, 0, len(array)-1)
	return array
}

func quickSortHelper(array []int, start, end int) {
	if end <= start {
		return
	}

	pivot := array[start]
	pos := end

	for i := pos; i > start; i-- {
		if array[i] > pivot {
			array[i], array[pos] = array[pos], array[i]
			pos--
		}
	}

	array[pos], array[start] = array[start], array[pos]

	quickSortHelper(array, start, pos-1)
	quickSortHelper(array, pos+1, end)

}
```




---

### Link:
- []()