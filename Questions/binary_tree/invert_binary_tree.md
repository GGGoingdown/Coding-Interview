# Invert Binary Tree

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

func (tree *BinaryTree) InvertBinaryTree() {
	if tree == nil {
		return
	}

	tree.Swap()
	tree.Left.InvertBinaryTree()
	tree.Right.InvertBinaryTree()

}
func (tree *BinaryTree) Swap() {
	tree.Left, tree.Right = tree.Right, tree.Left
}

```
---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/invert-binary-tree)