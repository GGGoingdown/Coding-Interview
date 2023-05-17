# BST Construction

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
// Recursive
type BST struct {
	Value int

	Left  *BST
	Right *BST
}

func (tree *BST) Insert(value int) *BST {
	if tree == nil {
		return &BST{Value: value}
	}

	if value < tree.Value {
		tree.Left = tree.Left.Insert(value)
	} else {
		tree.Right = tree.Right.Insert(value)
	}

	// Do not edit the return statement of this method.
	return tree
}

func (tree *BST) Contains(value int) bool {
	if tree == nil {
		return false
	}

	if tree.Value == value {
		return true
	}

	if value < tree.Value {
		return tree.Left.Contains(value)
	} else if value > tree.Value {
		return tree.Right.Contains(value)
	}

	return false
}


func (tree *BST) Remove(value int) *BST {
	if tree == nil {
		return nil
	}
	if value < tree.Value {
		tree.Left = tree.Left.Remove(value)
	} else if value > tree.Value {
		tree.Right = tree.Right.Remove(value)
	} else {
		if tree.Left == nil && tree.Right == nil {
			return nil
		}

		if tree.Left != nil && tree.Right == nil {
			tree.Value = tree.Left.Value
			tree.Right = tree.Left.Right
			tree.Left = tree.Left.Left
		} else if tree.Right != nil && tree.Left == nil {
			tree.Value = tree.Right.Value
			tree.Left = tree.Right.Left
			tree.Right = tree.Right.Right
		} else {
			smallValue := tree.Right.smallest()
			tree.Value = smallValue
			tree.Right = tree.Right.Remove(smallValue)
		}

	}

	// Do not edit the return statement of this method.
	return tree
}
func (tree *BST) smallest() int {
	if tree == nil {
		panic("Nil tree")
	}

	if tree.Left == nil {
		return tree.Value
	}

	return tree.Left.smallest()
}


```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/bst-construction)