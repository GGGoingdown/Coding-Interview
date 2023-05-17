# Heap sort

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

type heap []int

func (h heap) heapify() {
	start := len(h) / 2
	for start >= 0 {
		h.fixDown(start)
		start--
	}
}

func (h heap) fixDown(i int) {
	idx := i
	for !h.isLeaf(idx) {
		l := h.getLeftChildIdx(idx)
		if l < len(h)-1 && h[l] < h[l+1] {
			l++
		}
		if l < len(h) && h[idx] < h[l] {
			h[idx], h[l] = h[l], h[idx]
		}

		idx = l
	}
}

func (h heap) getLeftChildIdx(idx int) int {
	return 2*idx + 1
}

func (h heap) getRightChildIdx(idx int) int {
	return 2*idx + 2
}

func (h heap) getParentIdx(i int) int {
	return (i - 2) / 2
}

func (h heap) isLeaf(idx int) bool {
	l := len(h)
	if h.getLeftChildIdx(idx) > l && h.getRightChildIdx(idx) > l {
		return true
	}
	return false
}

func HeapSort(array []int) []int {
	h := heap(array)
	l := len(h)
	for l > 0 {
		h.heapify()
		h[0], h[len(h)-1] = h[len(h)-1], h[0]
		h = h[:len(h)-1]
		l--
	}

	return array
}

```

---

### Link:
- []()