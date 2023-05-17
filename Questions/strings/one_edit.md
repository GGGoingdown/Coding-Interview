# One Edit

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
// O(n) time | O(1) space, n is the length of longest string
func OneEdit(stringOne string, stringTwo string) bool {
	lenOne := len(stringOne)
	lenTwo := len(stringTwo)

	// replace method
	if lenOne == lenTwo {
		chance := 1
		for i := 0; i < len(stringOne); i++ {
			if stringOne[i] != stringTwo[i] {
				if chance == 0 {
					return false
				}
				chance--
			}
		}
		return true
	}
	// add or remove case
	var longStr string = stringOne
	var shortStr string = stringTwo
	if lenTwo > lenOne {
		longStr = stringTwo
		shortStr = stringOne
	}

	shortIdx := 0
	chance := 1
	for i := 0; i < len(longStr); i++ {
		if shortIdx >= len(shortStr) {
			if chance <= 0 {
				return false
			}
			chance--
			continue
		}

		if longStr[i] != shortStr[shortIdx] {
			if chance == 0 {
				return false
			}
			chance--
			continue
		}
		shortIdx++
	}

	return true
}
```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/one-edit)