# Reverse Words in string

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

import (
    "fmt"
    "strings"
)

func ReverseWordsInString(str string) string {
	sp := strings.Split(str, " ")
	result := ""
	for i := len(sp) - 1; i > -1; i-- {
		var s string
		if i == 0 {
			s = sp[i]
		} else {
			s = fmt.Sprintf("%s ", sp[i])
		}
		result += s
	}

	return result
}
```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/reverse-words-in-string)