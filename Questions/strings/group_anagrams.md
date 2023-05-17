# Group Anagrams

### Description:  
Anagrams are strings made up of exactly the same letters, where order doesn't matter. For example, "cinema" and "iceman" are anagrams;

**Sample input:**  
```
words = ["yo", "act", "flop", "tac", "foo", "cat", "oy", "olfp"]

```

**Sample output:**  
```
[["yo", "oy"], ["flop", "olfp"], ["act", "tac", "cat"], ["foo"]]
```


---
### Think :

---
### Solution
```go
type Group struct {
	idx   int
	count map[string]int
}

func GroupAnagrams(words []string) [][]string {
	group := make([][]string, 0, len(words))
	sum2group := make(map[int][]Group)

	for _, word := range words {
		sum := 0
		cc := make(map[string]int)

		for _, w := range word {
			sum += int(w)
			cc[string(w)]++
		}

		groups, ok := sum2group[sum]
		if ok {
		LOOP:
			for _, g := range groups {
				for key, val := range g.count {
					count, ok := cc[key]
					if !ok || count != val {
						group = append(group, []string{string(word)})
						sum2group[sum] = append(sum2group[sum], Group{
							idx:   len(group) - 1,
							count: cc,
						})
						break LOOP
					}
				}
				group[g.idx] = append(group[g.idx], word)
			}
		} else {
			// craete new
			group = append(group, []string{string(word)})
			sum2group[sum] = []Group{{idx: len(group) - 1, count: cc}}
		}

	}

	return group
}


```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/group-anagrams)