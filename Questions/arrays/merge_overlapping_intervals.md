# Mergee Overlapping Intervals

### Description:  
Write a function that takes in a non-empty array of arbitrary intervals, merges any overlapping intervals, and returns the
new intervals in no particular order.

Each interval interval is an array of two integers, with interval[0] as the start of the interval and interval[1]
as the end of the interval.

Note that back-to-back intervals aren't considered to be overlapping. For example, [1, 5] and [6, 7] aren't
overlapping: however, [1, 5] and [6, 7] are indeed overlapping.

Also note that the start of any particular interval will always be less than or equal to the end of that interval.

**Sample input:**  
```
intervals = [[1, 2], [3, 5], [4, 7], [6, 8], [9, 10]]
```

**Sample output:**  
```
[[1, 2], [3, 8], [9, 10]]
// merge the intervals [3, 5], [4, 7], [6, 8] into [3, 8]
```


---
### Think :
After sorting the intervals with respect to their starting values, traverse them, and at each iteration, compare the start of the next interval to the end of the current interval to look for an overlap. If you find an overlap, mutate the current interval so as to merge the next interval into it.
---
### Solution
```go
// O(nlogn) time |  O(n) space
import "sort"

func MergeOverlappingIntervals(intervals [][]int) [][]int {
	sort.Sort(ArrayByStart(intervals))
	output := make([][]int, 1)
	output[0] = intervals[0]

	for _, interval := range intervals{
		start, end := interval[0], interval[1]
		lastEnd := output[len(output)-1][1]
		if start > lastEnd{
			output = append(output, []int{start, end})
		}else{
			output[len(output)-1][1] = max(end, lastEnd)
		}

	}
	return output
}


func max(i, j int)int{
	if i>j{
		return i
	}
	return j
}

// Define a collection type that implements sort.Interface
type ArrayByStart [][]int

func (u ArrayByStart) Len() int {
	return len(u)
}
func (u ArrayByStart) Swap(i, j int) {
	u[i], u[j] = u[j], u[i]
}
func (u ArrayByStart) Less(i, j int) bool {
	return u[i][0] < u[j][0]
}

```




---

### Link:  
- [AlgoExpert](https://www.algoexpert.io/questions/merge-overlapping-intervals)