# Binary Tree Diameter

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

type BinaryTree struct {
	Value int

	Left  *BinaryTree
	Right *BinaryTree
}

func BinaryTreeDiameter(tree *BinaryTree) int {
	maxDiameter := 0
	CalculateDiameter(tree, &maxDiameter)
	return maxDiameter
}

func CalculateDiameter(tree *BinaryTree, max *int) int {
	if tree == nil {
		return 0
	}

	left := CalculateDiameter(tree.Left, max)
	right := CalculateDiameter(tree.Right, max)

	total := left + right
	if total > *max {
		*max = total
	}

	if left > right {
		return left + 1
	} else {
		return right + 1
	}
}


```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/binary-tree-diameter)