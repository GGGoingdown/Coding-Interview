# Array of products

### Description:  
Write a function that takes in a non-empty array of integers and returns an array of the same
length, where each element in the output array is equal to the product of every other number in
the input array.

In other words, the value at output [i] is equal to the product of every number in the input
array other than input [i] .

Note that you're expected to solve this problem without using division.

**Sample input:**  
```
array = [5, 1, 4, 2]

```

**Sample output:**  
```
[8, 40, 10, 20]
```


---
### Think :
第一個想法使用brute force解
第二種方法為優化解:
For each index in the input array, try calculating the product of every element to the left and the product of every element to the right. You can do this with two loops through the array: one from left to right and one from right to left.
---
### Solution
```go
// brute force 
// O(n^2) time | O(n) space

func ArrayOfProducts(array []int) []int {
	result := make([]int, len(array))

	for i:=0; i<len(array);i++{
		product := 1
		for j:=0; j<len(array);j++{
			if j != i{
				product*= array[j]
			}
		}
		result[i] = product
	}

	return result
}

```
```go
// O(n) time | O(n) space

func ArrayOfProducts(array []int) []int {
	result := make([]int, len(array))


	product := 1
	for i:=0; i<len(array);i++{
		result[i] = product
		product*= array[i]
	}

	product = 1
	for i:=len(array)-1; i>=0; i--{
		result[i]*= product
		product *= array[i]
	}

	return result
}
```

---

### Link:  
- [AlgoExpert](https://www.algoexpert.io/questions/array-of-products)