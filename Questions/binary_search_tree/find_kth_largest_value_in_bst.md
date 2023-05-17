# Find Kth Largest Value in BST

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

func (t *BST) Inorder(array []int) []int {
	if t == nil {
		return array
	}

	array = t.Left.Inorder(array)
	array = append(array, t.Value)
	array = t.Right.Inorder(array)
	return array
}

func FindKthLargestValueInBst(tree *BST, k int) int {
	values := make([]int, 0, 10)
	values = tree.Inorder(values)
	return values[len(values)-k]
}
```

---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/find-kth-largest-value-in-bst)
