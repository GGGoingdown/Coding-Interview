# Question

### Description:  
Write a function that takes in an n x m two-dimensional array (that can be square-shaped when n ==m) and returns a
one-dimensional array of all the array's elements in spiral order.

Spiral order starts at the top left corner of the two-dimensional array, goes to the right, and proceeds in a spiral pattern
all the way until every element has been visited.

**Sample input:**  
```
array = [
    [1, 2, 3, 4],
    [12, 13, 14, 5],
    [11, 16, 15, 6],
    [10, 9, 8, 7]
]
```

**Sample output:**  
```
[1, 2, 3, 4, 5 ,6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16]
```

---
### Think :  
You can think of the spiral that you have to traverse as a set of rectangle perimeters that progressively get smaller (i.e., that progressively move inwards in the two-dimensional array).
Declare four variables: a starting row, a starting column, an ending row, and an ending column.
These four variables represent the bounds of the first rectangle perimeter in the spiral that you have to traverse.
Traverse that perimeter using those bounds, and then move the bounds inwards. End your algorithm once the
starting row passes the ending row or the starting column passes the ending column.
You can solve this problem both iteratively and recursively following very similar logic.
---
### Solution
```go
// O(n) time | O(n) space
func SpiralTraverse(array [][]int) []int {

	result := make([]int, 0)
	sR, sC, eR, eC := 0, 0, len(array)-1, len(array[0])-1

	for sR <= eR && sC <= eC {
		traverseHelper(sR, sC, eR, eC, &result, array)

		sR++
		eR--
		sC++
		eC--

	}

	return result
}

func traverseHelper(sR, sC, eR, eC int, result *[]int, array [][]int) {
	// Top row
	for i := sC; i <= eC; i++ {
		val := array[sR][i]
		*result = append(*result, val)
	}
	// Right column
	for i := sR + 1; i <= eR; i++ {
		val := array[i][eC]
		*result = append(*result, val)
	}
	// Down row
	if sR != eR {
		for i := eC - 1; i >= sC; i-- {
			val := array[eR][i]
			*result = append(*result, val)
		}
	}

	// Left column
	if sC != eC {
		for i := eR - 1; i > sR; i-- { 
			val := array[i][sC]
			*result = append(*result, val)
		}
	}
}

```




---

### Link:  
- [AlgoExpert](https://www.algoexpert.io/questions/spiral-traverse)