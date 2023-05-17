# Sorted Squared Array

### Description:  
Write a function that takes in a non-empty array of integers that are sorted in
ascending order and returns a new array of the same length with the squares of
the original integers also sorted in ascending order.

**Sample input:**  
```
array = [1, 2, 3, 5, 6, 8, 9]
```

**Sample output:**  
```
[1, 4, 9, 25, 36, 64, 91]
```


---
### Think :
這題目需要注意的是負數, 因為input array是一個ascending order,
而且題目要求我們返回時也是ascending order  
最直接的想法是, 把每個值做squared之後, 返回前做排序, 但這樣的`time complexity = O(nlogn)`, 於是思考有沒有O(n)的解法  



---
### Solution
```go
// O(n) time | O(n) space, n is the length of array

func SortedSquaredArray(array []int) []int {
	// Create output array with same length as input array
	output := make([]int, len(array))

	// Set pointers to left and right side of array
	l, r := 0, len(array)-1

	// Set starting index for output array
	currentIndex := len(output) - 1

	// Iterate through the array in reverse order
	for l <= r {
		// Get the absolute values of the left and right pointers
		l_abs := math.Abs(float64(array[l]))
		r_abs := math.Abs(float64(array[r]))

		var squaredNum int

		// If the left absolute value is greater than the right absolute value, square the left value
		// and move the left pointer up one space
		if l_abs > r_abs {
			squaredNum = int(l_abs) * int(l_abs)
			l++
		} else {
			// Otherwise, square the right value and move the right pointer down one space
			squaredNum = int(r_abs) * int(r_abs)
			r--
		}

		// Set the current index in the output array to the squared value
		output[currentIndex] = squaredNum
		// Move the current index down one space
		currentIndex--

	}

}


```




---

### Link:
- [Algoexpert](https://www.algoexpert.io/questions/sorted-squared-array)