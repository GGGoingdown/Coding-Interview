# Three number sort

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
func ThreeNumberSort(array []int, order []int) []int {
	result := make([]int, len(array))
	counter := make(map[int]int)
	for _, val := range array{
		counter[val]++
	}

	curIdx := 0
	for _, num := range order{
		count := counter[num]
		for count > 0{
			result[curIdx] = num
			count--
			curIdx++
		}
	}

	return result
}
```

---
### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/three-number-sort)