# Min Height BST

### Description:  


**Sample input:**  
```

```

**Sample output:**  
```
```


---
### Think :

---
### Solution
```go
type BST struct {
	Value int

	Left  *BST
	Right *BST
}


func MinHeightBST(array []int) *BST {
	// The left end of the array
	left := 0
	// The right end of the array
	right := len(array) - 1
	// The middle of the array
	mid := (right + left) / 2

	// If the left end is greater than the right end, 
	// return nil
	if left > right{
		return nil 
	}

	// Create a new node with the value of the middle 
	// element of the array
	node := &BST{Value: array[mid]}

	// Set the left node of the current node to the 
	// result of the recursive call on the left half 
	// of the array
	node.Left = MinHeightBST(array[:mid])
	// Set the right node of the current node to the 
	// result of the recursive call on the right half 
	// of the array
	node.Right = MinHeightBST(array[mid+1:])

	// Return the node
	return node
}

```

---

### Link:
- []()