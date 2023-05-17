# Run-Length Encoding

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

func RunLengthEncoding(str string) string {
	count := 1
	var curS byte = str[0]

	result := ""

	for _, s := range str[1:] {
		if byte(s) != curS {
			result += fmt.Sprintf("%d%s", count, string(curS))
			count = 0
		}
		curS = byte(s)
		count++
		if count >= 10 {
			result += fmt.Sprintf("9%s", string(curS))
			count = 1
		}
	}

	result += fmt.Sprintf("%d%s", count, string(curS))

	return result
}



```




---

### Link:
