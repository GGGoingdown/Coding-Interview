# Validate Subsequence

### Description:  
Given two non-empty arrays of integers, write a function that determines whether
the second array is a subsequence of the first one.

A subsequence of an array is a set of numbers that aren't necessarily adjacent in
the array but that are in the same order as they appear in the array. For instance,
the numbers [1, 3, 4] form a subsequence of the array [1, 2, 3, 4]
and so do the numbers [2，4] • Note that a single number in an array and the
array itself are both valid subsequences of the array.

**Sample input:**  
```
array = [5, 1, 22, 25, 6, -1, 8 , 10]
seq = [1, 6, -1, 10]

```

**Sample output:**  
```go
true
```

---
### Think
先確認以下三種情況,如果發生則直接返回
1. array的長度等於0
2. sequence的長度等於0
3. sequence的長度大於array的長度(sequence不成立)

由於題目要求順序也要相同,所以直接走遍`array`, 指定一個指針在sequence index=0上,
當`array`的值等於`sequence`時, index++, 當index的長度大於sequence的長度時,則返回true, 反之如果`array`走完,則返回false

---
### Solution
```go
// O(n) time | O(1) space, n is the length of array
func IsValidSubsequence(array []int, sequence []int) bool {
	// Check if we have a valid input
	if len(array) == 0 || len(sequence) == 0 || len(sequence) > len(array){
		return false
	}

	// Initialize a sequence pointer to keep track of where we are in the sequence
	seqPoint := 0
	seqLength := len(sequence)

	// Iterate through the array
	for _, v := range array{
		// If the current value equals the current sequence value
		if v == sequence[seqPoint]{
			// Increment the sequence pointer
			seqPoint++

			// If the sequence pointer equals the sequence length, we have found the sequence
			if seqPoint == seqLength{
				return true
			}
		}
	}
}
```


---
### Link:
- [Algoexpert](https://www.algoexpert.io/questions/validate-subsequence)