# Longest Palindromic Substring

### Description:  
A palindrome is defined as a string that's written the same forward and backward. Note that single-character strings are palindromes.

You can assume that there will only be one longest palindromic substring.
**Sample input:**  
```
string = "abaxyzzyxf"
```

**Sample output:**  
```
xyzzyx
```


---
### Think :

---
### Solution
```go
func LongestPalindromicSubstring(str string) string {
	longest := ""
	for i := 0; i < len(str)-1; i++ {
		for j := i + 1; j < len(str); j++ {
			if str[i] == str[j] {
				left := i
				right := j
				for left < right {
					left++
					right--
					if left+1 == right-1 || left+1 == right {
						cur := str[i : j+1]
						if len(cur) > len(longest) {
							longest = cur
						}
					}
				}
			}
		}
	}

	return longest
}


```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/longest-palindromic-substring)