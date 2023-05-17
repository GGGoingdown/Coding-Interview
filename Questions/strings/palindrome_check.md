# Palindrome check

### Description:  
Write a function that takes in a non-empty string and that returns a boolean representing whether the string is a palindrome.

**Sample input:**  
```
string = "abcdcba"
```

**Sample output:**  
```
true
```


---
### Think :
利用two-pointer來讀字串的頭跟尾，如果有不同則代表不適palindrome
---
### Solution
```go
func IsPalindrome(s string) bool {
	r := []rune(s)
	left := 0
	right := len(r) - 1

	for left < right {
		if r[left] != r[right] {
			return false
		}
		left++
		right--
	}

	return true
}
```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/palindrome-check)