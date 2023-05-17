# Move element to end

### Description:  
You're given an array of integers and an integer. Write a function that moves all
instances of that integer in the array to the end of the array and returns the array.

The function should perform this in place (i.e., it should mutate the input array)
and doesnit need to maintain the order of the other integers.

**Sample input:**  
```
array = [2, 1, 2, 2, 2, 3, 4, 2]
toMove = 2
```

**Sample output:**  
```
[1, 3, 4, 2, 2, 2, 2, 2] // the numbers 1, 3 and 4 could be ordered differently
```


---
### Think :
Set two pointers at the start and end of the array, respectively. Move the right pointer inwards so long as it points to the integer to move, and move the left pointer inwards so long as it doesn't point to the integer to move. When both pointers aren't moving, swap their values in place. Repeat this process until the pointers pass each other.
---
### Solution
```go
// O(n) time | O(1) space
func MoveElementToEnd(array []int, toMove int) []int {
	// empty array
	if len(array) == 0{
		return array
	}

	// two pointers
	l, r := 0, len(array) -1
	// loop until two pointers meet
	for l < r{
		// if left pointer is not toMove, move it to right
		if array[l] != toMove{
			l++
			continue
		}

		// if right pointer is toMove, move it to left
		if array[r] == toMove{
			r--
			continue
		}

		// swap l and r
		array[l], array[r] = array[r], array[l]
	}

	return array
}

```

---

### Link:
- [Algoexpert](https://www.algoexpert.io/questions/move-element-to-end)