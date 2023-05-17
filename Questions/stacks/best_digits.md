# Best Digits

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
// O(n) time | O(n) space, n is the length of input number
func BestDigits(number string, numDigits int) string {
	stack := make([]rune, 0)
	for _, num := range number {
		if numDigits > 0 && len(stack) > 0 {
			if num == 48 { // equal to zero
				numDigits--
				continue
			}
			if num >= stack[len(stack)-1] {
				stack = stack[:len(stack)-1]
				numDigits--
			}
		}
		stack = append(stack, num)
	}

	for numDigits > 0 {
		stack = stack[:len(stack)-1]
		numDigits--
	}

	return string(stack)
}


```


---

### Link:
- [ALgoExpert](https://www.algoexpert.io/questions/best-digits)