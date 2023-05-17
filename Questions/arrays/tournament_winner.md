# Tournament Winner

### Description:  
Given an array of pairs representing the teams that have competed against each
other and an array containing the results of each competition, write a function
that returns the winner of the tournament. The input arrays are named
competitions and resultsrespectively. The competitions array has
elements in the form of [homeTeam, awayTeam] where each team is a string
of at most 30 characters representing the name of the team. The results
array contains information about the winner of each corresponding competition
in the competitions array. Specifically, results[i] denotes the winner of
competitions[i] , where a 1 in the results array means that the home
team in the corresponding competition won and a @ means that the away team a
won.

It's guaranteed that exactly one team will win the tournament and that each team
will compete against all other teams exactly once. It's also guaranteed that the
tournament will always have at least two teams.

**Sample input:**  
```
competitions = [
    ["HTML", "C#"],
    ["C#", "Python"],
    ["Python", "HTML]
]
results = [0, 0, 1]

```

**Sample output:**  
```
"Python"

```
---
### Think :
Loop through all of the competitions, and update the hash table at every
iteration. For each competition, consider the name of the winning team: if
the name already exists in the hash table, update that entry by adding 3
points to lt. If the team name doesn't exist in the hash table, add a new
entry in the hash table with the key as the team name and the value as 3
(since the team won its first competition). While looping through all of the
competitions, keep track of the team with the highest score, and at the end
of the algorithm, return the team with the highest score.


---
### Solution
```go
// O(n) time | O(k) space,  n is the number of competitions,  k is the number of teams
const HOME_TEAM_WON = 1

func TournamentWinner(competitions [][]string, results []int) string {
	// Create a map of teams and assign 0 as the initial score
	dashBoard := make(map[string]int)
	var winner string
	var winderScore int

	// Loop through the competitions slice
	for idx, compcompetition := range competitions{
	// Check if the result for the competition is home team won
		var team string
		if results[idx] == HOME_TEAM_WON{
		// Add the home team to the map and increment the score by 3
			team = compcompetition[0]
			dashBoard[team]++
		}else{
		// Add the away team to the map and increment the score by 3
			team = compcompetition[1]
			dashBoard[team]++
		}

	// Check if the score for the team is greater than the current winner
		if score, ok := dashBoard[team];ok{
			if score > winderScore{
				winner = team
				winderScore = score
			}
		}

	}

	return winner
}

```




---

### Link:
- [AlgoExpert](https://www.algoexpert.io/questions/tournament-winner)