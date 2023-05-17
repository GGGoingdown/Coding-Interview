# Common Characters

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
func CommonCharacters(strings []string) []string {
	table := make(map[string]int)
	result := make([]string, 0)

	for _, s := range strings[0] {
		table[string(s)] = 0
	}

	for i, ss := range strings[1:] {
		for _, s := range ss {
			if v, ok := table[string(s)]; ok {
				if v == i {
					table[string(s)]++
				}
			}
		}
	}
	for k, v := range table {
		if v == len(strings)-1 {
			result = append(result, k)
		}
	}

	return result
}
```

---

### Link:
