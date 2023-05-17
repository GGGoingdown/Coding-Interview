# First Duplicate Value

### Description:  
Given an array of integers between 1 and n . inclusive, where n is the length of the array, write a function that
returns the first integer that appears more than once (when the array is read from left to right).

In other words, out of all the integers that might occur more than once in the input array, your function should return the
one whose first duplicate value has the minimum index.

If no integer appears more than once, your function should return -1

Note that you're allowed to mutate the input array.

**Sample input:**  
```
array = [2, 1, 5, 2, 3, 3, 4]
```

**Sample output:**  
```
2
```


---
### Think :
Since the integers are between 1 and the length of the input array, you can map them to indices in the array itself by subtracting 1 from them. Once you've mapped an integer to an index in the array, you can mutate the value in the array at that index and make it negative (by multiplying it by -1). Since the integers normally aren't negative, the first time that you encounter a negative value at the index that an integer maps to, you'll know that you'll have already seen that integer.
---
### Solution
```go
// O(n) time | O(1) space
func FirstDuplicateValue(array []int) int {
	for i:=0; i<len(array);i++{
		idx := math.Abs(float64(array[i])) - 1
		if array[int(idx)] < 0{
			return int(math.Abs(float64(array[i])))
		}
		array[int(idx)] = array[int(idx)] * -1
	}
	return -1
}	

```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/first-duplicate-value)