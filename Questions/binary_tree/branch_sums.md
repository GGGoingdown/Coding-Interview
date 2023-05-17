# Branch Sums

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
// This is the struct of the input root. Do not edit it.
type BinaryTree struct {
	Value int
	Left  *BinaryTree
	Right *BinaryTree
}

func BranchSums(root *BinaryTree) []int {

	result := make([]int, 0, 10)
	branchSumsHelper(root, 0, &result)

	return result
}

func branchSumsHelper(root *BinaryTree, sum int, records *[]int) {
	if root == nil {
		return
	}

	if root.Left == nil && root.Right == nil {
		sum += root.Value
		*records = append(*records, sum)
		return
	}

	sum += root.Value
	branchSumsHelper(root.Left, sum, records)
	branchSumsHelper(root.Right, sum, records)

}
```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/branch-sums)