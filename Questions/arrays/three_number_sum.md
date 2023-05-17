# Three Number Sum

### Description:  
Write a function that takes in a non-empty array Ot distinct integers and an integer
representing a target sum. The function should find all triplets in the array that
sum up to the target sum and return a two-dimensional array of all these triplets.
The numbers in each triplet should be ordered in ascending order, and the triplets
themselves should be ordered in ascending order with respect to the numbers
they hold.

If no three numbers sum up to the target sum, the function should return an
empty array.

**Sample input:**  
```
array = [12, 3, 1, 2, -6, 5, -8, 6]
targetSum = 0
```

**Sample output:**  
```
[[-8 2 6] [-8 3 5] [-6 1 5]]
```
---
### Think :
Try sorting the array and traversing it once. At each number, place a left
pointer on the number immediately to the right of your current number
and a right pointer on the final number in the array. Check if the current
number, the left number, and the right number sum up to the target sum.
Since the array is now sorted, you know that moving the left
pointer mentioned blow one place to the right wil lead to a greater
left number and thus a greater sum. Similarly, you know that moving the
right pointer one place to the left will lead to a smaller right number and
thus a smaller sum. This means that, depending on the size of each triplet's
(current number, left number, right number) sum relative to the target
sum, you should either move the left pointer, the right pointer, or both to
obtain a potentiallv valid triplet.
---
### Solution
```go
// O(n^2) time | O(n) space, n is the length of the input array
func ThreeNumberSum(array []int, target int) [][]int {
	output := make([][]int, 0)

	// make a copy of the input array
	newArray := make([]int, len(array))
	copy(newArray, array)

	// sort the array in ascending order
	sort.Ints(newArray)

	// iterate over each element of the array
	for idx, val := range newArray{

		// set left pointer to one index above current element
		l := idx+1

		// set right pointer to last element of array
		r := len(newArray) - 1

		// while left pointer is less than right pointer
		for l < r{

			// find the sum of the current element, left pointer, and right pointer
			sum := val + newArray[l] + newArray[r]

			// if the sum is less than target
			if sum < target{

				// move left pointer up one spot
				l++

			// if the sum is greater than target
			}else if sum > target{

				// move right pointer down one spot
				r--

			// if the sum is equal to target
			}else if sum == target{

				// append the three elements to the output array
				output = append(output, []int{val, newArray[l], newArray[r]}) 

				// move left pointer up one spot
				l++

				// move right pointer down one spot
				r--
			}
		}
	}

	// return the output array
	return output
}
```




---

### Link:
- [Algoexpert](https://www.algoexpert.io/questions/three-number-sum)