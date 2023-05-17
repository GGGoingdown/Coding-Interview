# Question

### Description:  
Write a function that takes in an array of integers and returns a boolean representing whether the array is monotonic.

An array is said to be monotonic if its elements, from left to right, are entirely non-increasing or entirely non-decreasing.

Non-increasing elements aren't necessarily exclusively decreasing; they simply don't increase. Similarly, non-decreasing
elements aren't necessarily exclusively increasing; they simply don't decrease.

Note that empty arrays and arrays of one element are monotonic.

**Sample input:**  
```
array = [-1, -5, -10, -1100, -1100, -1101, -1102, -9001]
```

**Sample output:**  
```
true
```


---
### Think :
You can start by assuming that the array is both entirely non-decreasing and entirely non-increasing.
Asyou iterate through each element, perform a check to see if you can invalidate one or both of your assumptions.
---
### Solution
```go
// O(n) time | O(1) space
func IsMonotonic(array []int) bool {
	// check if the array is at least 2 elements long
	if len(array) <2{
		return true
	}

	// create a counter to keep track of the number of increases and decreases
	increaseCounter := 0
	decreaseCounter := 0

	// start at the first element
	l := 0

	// iterate through the array
	for i:=1; i<len(array);i++{
		// get the left and right values
		lVal := array[l]
		rVal := array[i]
		// check if the left value is greater than the right value
		if lVal > rVal{
			// if it is, increase the decrease counter
			decreaseCounter++
		}else if lVal < rVal{
			// if it is, increase the increase counter
			increaseCounter++
		}
		// move the left pointer to the right
		l = i
	}


	// if the increase counter is greater than 0 and the decrease counter is greater than 0
	if increaseCounter !=0 && decreaseCounter != 0{
		// return false
		return false
	}
	// return true
	return true
}


```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/monotonic-array)