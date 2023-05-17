# Two Number sum

### Description:  
Write a function that takes in a non-empty array of distinct integers and an integer representing a target sum. If any (WO
numbers in the input array sum up to the target sum, the function should return them in an array, in any order. If no two
numbers sum up CO the target sum, the function should return an empty array.

Note that the target sum has to be obtained by summing tWo different integers in the array: you cant add a single
integer to itself in order to obtain the target sum.

You can assume that there will be at most one pair of numbers summing up to the target sum.

**Sample input:**  
```
array = [3, 5, -4, 8, 11, 1, -1, 6]
targetSum: 10
```

**Sample output:**  
```
[-1, 11]
```

---
### Think: 
利用`hash table`來儲存走過的值,當`remaining`在table裡則返回true


---
### Solution:  
```go
// O(n) time | O(n) space, n is the length of array
func TwoNumberSum(array []int, target int) []int {
	result := make([]int, 0, 2) // This is the array that will hold the result
	table := make(map[int]struct{}) // This is the hash table we will use to track the values we have seen in the array

	for _, v := range array{ // Iterate over the array
		remaining := target - v // Calculate the remaining value we need to add up to the target
		if _, ok := table[remaining];ok{ // Check if we have seen the remaining value
			result = append(result, v, remaining) // If we have seen the remaining value, it means we have found the pair of numbers we need
			return result // Return the result
		}

		table[v] = struct{}{} // If we haven't seen the remaining value, add the current value to the table
	}
}
```

---

### Link:

- [Algoexpert](https://www.algoexpert.io/questions/two-number-sum)