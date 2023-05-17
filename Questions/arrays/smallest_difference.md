# Smallest Difference

### Description:  
Write a function that takes in two non-empty arrays of integers, finds the pair of
numbers (one from each array) whose absolute difference is closest to zero, and
returns an array containing these two numbers, with the number from the first
array in the first position.

Note that the absolute difference of two integers is the distance between them on
the real number line. For example, the absolute difference of -5 and 5 is 10, and
the absolute difference of -5 and -4is 1.

You can assume that there will only be one pair of numbers with the smallest
difference.

**Sample input:**  
```
arrayOne = [-1, 5, 10, 20, 28, 3]
arrayTwo = [26, 134, 135, 15, 17]

```

**Sample output:**  
```
[28, 26]
```


---
### Think :
Start by sorting both arrays, as per Hint #2. Put a pointer at the beginning of both arrays and evaluate the absolute difference of the pointer-numbers. If the difference is equal to zero, then you have found the closest pair; otherwise, increment the pointer of the smaller of the two numbers to find a potentially better pair. Continue until you get a pair with a difference of zero or until one of the pointers gets out of range of its array.
---
### Solution
```go
// O(nlogn) + O(mlogm), n is length of array1, m is length of array2
// O(1) space
import (
    "sort"
    "math"
)

func SmallestDifference(array1, array2 []int) []int {
    // Sort both arrays
    sort.Ints(array1)
    sort.Ints(array2)

    // Set two pointers
    l, r := 0, 0
    minDif := math.Inf(1)
    result := make([]int, 2)

    // Iterate through both arrays
    for l < len(array1) && r < len(array2){
        // Calculate absolute difference
        dif := math.Abs(float64(array1[l] - array2[r]))
        // Update minDif and result if necessary
        if dif < minDif{
            minDif = dif
            result[0], result[1] = array1[l], array2[r]
        }

        // Move pointer
        if array1[l] < array2[r]{
            l++
        }else{
            r++
        }
    }
    return result
}
```
---

### Link:
- [Algoexpert](https://www.algoexpert.io/questions/smallest-difference)