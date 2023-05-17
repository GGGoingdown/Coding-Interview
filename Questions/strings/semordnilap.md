# Semordnilap

### Description:  
A semordnilap pair is defined as a set of different strings where the reverse of one world is the same as the forward version of the other. For example the words "diaper" and "repaid" are a semordnilap pair, as are the words "pailndromes" and "semordnilap".

**Sample input:**  
```
words = ["diaper", "abc", "test", "cba", "repaid"]
```

**Sample output:**  
```
[["diaper", "repaid"], ["abc", "cba"]]
```


---
### Think :

---
### Solution 1
```go

func Semordnilap(words []string) [][]string {
	sumWords := make(map[int][]string)
	result := make([][]string, 0)

	for _, word := range words {
		sum := 0
		for _, w := range word {
			sum += int(w)
		}
		matchingWords, ok := sumWords[sum]
		if !ok {
			sumWords[sum] = append(sumWords[sum], word)
		} else {
		LOOP:
			for _, matchingWord := range matchingWords {
				for i := 0; i < len(matchingWord); i++ {
					pointer := len(word) - 1 - i
					if word[pointer] != matchingWord[i] {
						break LOOP
					}
				}
				result = append(result, []string{matchingWord, word})
			}
		}
	}

	return result
}
```

### Solution 2
```go
// O(n * m) time | O(n), n is the number of words, m is the length of longest word
func Semordnilap(words []string) [][]string {
	set := make(map[string]struct{})
	var result [][]string

	for _, word := range words {
		set[string(word)] = struct{}{}
	}

	for _, word := range words {
		revWrod := reverseWord(string(word))
		_, ok := set[revWrod]
		if ok && word != revWrod {
			result = append(result, []string{string(revWrod), string(word)})
			delete(set, string(word))
			delete(set, string(revWrod))
		}
	}

	return result
}

func reverseWord(word string) string {
	rWrod := []rune(word)
	length := len(rWrod)
	if length <= 1 {
		return word
	}

	for i, j := 0, length-1; i < j; i, j = i+1, j-1 {
		rWrod[i], rWrod[j] = rWrod[j], rWrod[i]
	}

	return string(rWrod)
}
```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/semordnilap)