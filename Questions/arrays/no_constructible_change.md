# No-constructible change

### Description:  
Given an array of positive integers representing the values of coins in your
possession, write a function that returns the minimum amount of change (the
minimum sum of money) that you cannot create. The given coins can have any
positive integer value and aren't necessarily unique (.e., you can have multiple
coins of the same value).

For example, if you're given coins = [1, 2, 5] the minimum amount of
change that you cant create is 4 . If you're given no coins, the minimum amount
of change that you can't create is

**Sample input:**  
```
coins = [5, 7, 1, 1, 2, 3, 22]
```

**Sample output:**  
```
20
```


---
### Think :
Create a variable to store the amount of change that you can currently create up to. Sort all of your coins, and loop through them in ascending order. At every iteration, compare the current coin to the amount of change that you can currently create up to. Here are the two scenarios that you will encounter:
 
- The coin value is greater than the amount of change that you can currently create plus 1.
- The coin value is smaller than or equal to the amount of change that you can currently create plus 1.

In the first scenario, you simply return the current amount of change that you can create plus 1, because you can't create that amount of change. In the second scenario, you add the value of the coin to the amount of change that you can currently create up to, and you continue iterating through the coins.
The reason for this is that, if you're in the second scenario, you can create all of the values of change that you can currently create plus the value of the coin that you just considered. If you're given coins [1, 2] , then you can make 1, 2, 3 cents. So if vou add a coin of value 4 then vou can make 1 4 + 1 cents, 4 + 2 cents, and 4 +3 cents. Thus, you can make up to 7 cents.


---
### Solution
```go
// O(nlogn) time | O(1) space
// The function takes in an array of coins
func NonConstructibleChange(coins []int) int {
	// If the array is empty, return 1
	if len(coins) == 0{
		return 1
	}
	
	// We sort the array so that we can iterate through it in ascending order
	sort.Ints(coins)

	// We initialize the change variable to 0
	var change int = 0

	// We iterate through the array
	for _, val := range coins{
		// If the value is greater than the change + 1 (which is the smallest amount we can't create)
		if val > change + 1{
			// Return the change + 1
			return change + 1
		}

		// Otherwise, add the value to the change
		change += val
	}

	// Return the change + 1
	return change + 1
}

```




---

### Link:
- [Algoexpert](https://www.algoexpert.io/questions/non-constructible-change)