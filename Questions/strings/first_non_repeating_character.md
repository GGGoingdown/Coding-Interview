# First Non-Repeating Character

### Description:  
Write a function that takes in a string of lowercase English-alphabet letters and returns the index of the strings's first non-repeating character
if the input string doesn't have any nhon-repeating characters, your function should return -1

**Sample input:**  
```
string = "abcdcaf"

```

**Sample output:**  
```
1 // The first non-repeating character is "b"
```


---
### Think :

---
### Solution
```go

func FirstNonRepeatingCharacter(str string) int {
	count := make(map[string]int)

	for _, char := range str {
		_, ok := count[string(char)]
		if ok {
			count[string(char)]++
		} else {
			count[string(char)] = 0
		}
	}

	for i, char := range str {
		counter := count[string(char)]
		if counter == 0 {
			return i
		}
	}

	return -1
}
```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/first-non-repeating-character)