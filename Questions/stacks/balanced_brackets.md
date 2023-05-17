# Balanced Brackets

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
// O(n) time | O(n) space, n is the length of string
func BalancedBrackets(s string) bool {
	backBrackets := map[string]string{
		"]": "[",
		")": "(",
		"}": "{",
	}
	foreBrackets := map[string]struct{}{
		"{": struct{}{},
		"(": struct{}{},
		"[": struct{}{},
	}

	stack := make([]string, 0)
	for _, s := range s {
		_, ok := foreBrackets[string(s)]
		if ok {
			// add forebracket
			stack = append(stack, string(s))
		} else {
			bracket, ok := backBrackets[string(s)]
			if ok {
				if len(stack) == 0 {
					return false
				}
				last := stack[len(stack)-1]
				if last != bracket {
					return false
				}
				stack = stack[:len(stack)-1]
			}
		}

	}

	return len(stack) == 0
}

```

---
### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/balanced-brackets)