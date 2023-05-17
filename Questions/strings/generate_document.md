# Geberate Document

### Description:  
You're only able to generate the document if the frequency of unique characters in the characters string is greater than or equal to the frequency of unique characters in the document string.

**Sample input:**  
```
characters = "abcabc"
document = "aabbccc"
```

**Sample output:**  
```
false // missing one c
```


---
### Think :

---
### Solution
```go

func GenerateDocument(characters string, document string) bool {
	charT := make(map[string]int)
	docT := make(map[string]int)

	for _, v := range document {
		docT[string(v)]++
	}
	for _, v := range characters {
		charT[string(v)]++
	}

	for k, v := range docT {
		count, ok := charT[k]
		if !ok {
			return false
		}
		if ok && v > count {
			return false
		}
	}
	return true
}

```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/generate-document)