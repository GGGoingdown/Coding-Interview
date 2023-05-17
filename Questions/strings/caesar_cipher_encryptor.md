# Caesar Cipher Encryptor

### Description:  
Given a non-empty string of lowercase letters and a non-negative integer representing a key, write a function that returns a new string obtained by shifting every letter in the input string by k positions in the alphabet, where k is the key.
Note that letters should "wrap" around the alphabet;the letter z shifted by one returns the letter a.

**Sample input:**  
```
string = "xyz", key = 2
```

**Sample output:**  
```
zab
```


---
### Think :

---
### Solution
```go

func CaesarCipherEncryptor(s string, key int) string {
	run := key % 26 // 26 lower letters
	result := make([]byte, len(s))

	for i, v := range s {
		ss := int(v) + run
		if ss > 122 {
			remain := (ss - 122) - 1
			result[i] = byte(97 + remain)
			continue
		}
		result[i] = byte(ss)
	}

	return string(result)
}


```

---

### Link:
