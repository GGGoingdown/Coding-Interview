# Validate BST

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


func (tree *BST) ValidateBst() bool {
	min := -(1<<63 - 1)
	max := 1<<63 - 1

	return validBST(tree, min, max)

}



func validBST(tree *BST, min, max int)bool{
	if tree == nil{
		return true
	}

	if tree.Value < min || tree.Value >= max{
		return false
	}

	return validBST(tree.Left, min, tree.Value) && validBST(tree.Right, tree.Value, max)
}


```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/validate-bst)