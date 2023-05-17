# Minimum characters for words

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
func MinimumCharactersForWords(words []string) []string {
	gCounter := make(map[string]int)
	lCounter := make(map[string]int)
	result := make([]string, 0)

	for _, word := range words {
		for _, char := range word {
			lCounter[string(char)]++
		}
		for k, v := range lCounter {
			c, ok := gCounter[k]
			if !ok {
				gCounter[k] = v
			} else {
				if v > c {
					gCounter[k] = v
				}
			}
		}
		lCounter = make(map[string]int)
	}

	for char, count := range gCounter {
		for count > 0 {
			result = append(result, char)
			count--
		}
	}

	return result
}

```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/minimum-characters-for-words)