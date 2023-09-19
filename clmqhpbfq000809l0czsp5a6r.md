---
title: "Daily Temperatures - Leetcode 739"
datePublished: Tue Sep 19 2023 15:48:32 GMT+0000 (Coordinated Universal Time)
cuid: clmqhpbfq000809l0czsp5a6r
slug: leetcode-0739
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695138453432/3c94c7fd-80fe-40e1-ab72-d3b0f2f761d6.png
tags: go, leetcode

---

# Problem - Leetcode

Given an array of integers `temperatures` represent the daily temperatures, return *an array*`answer` *such that* `answer[i]` *is the number of days you have to wait after the* `i<sup>th</sup>` *day to get a warmer temperature*. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

**Example 1:**

```go
Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]
```

**Example 2:**

```go
Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]
```

**Example 3:**

```go
Input: temperatures = [30,60,90]
Output: [1,1,0]
```

**Constraints:**

* `1 <= temperatures.length <= 10<sup>5</sup>`
    
* `30 <= temperatures[i] <= 100`
    

# Solution in Golang

```go
func dailyTemperatures(temperatures []int) []int {
	res := make([]int, len(temperatures))
	for i := len(temperatures) - 1; i >= 0; i-- {
		j := i + 1
		for j < len(temperatures) && temperatures[j] <= temperatures[i] {
			if res[j] <= 0 {
				break
			}
			j += res[j]
		}
		if j < len(temperatures) && temperatures[j] > temperatures[i] {
			res[i] = j - i
		}
	}
	return res
}
```

This code defines a Go function called `dailyTemperatures` that takes a slice of integers called `temperatures` as input and returns another slice of integers as output. The purpose of this function is to calculate the number of days you have to wait until a warmer temperature is forecasted for each day in the input.

Here's a detailed explanation of how the code works:

1. `res := make([]int, len(temperatures))`: This line initializes an integer slice called `res` with the same length as the input `temperatures`. This slice will store the number of days to wait for a warmer temperature for each day in the input.
    
2. The code then enters a loop that iterates through the `temperatures` slice in reverse order, starting from the last day and moving towards the first day: `for i := len(temperatures) - 1; i >= 0; i--`.
    
3. Inside this loop, a variable `j` is initialized to `i + 1`. `j` will be used to traverse through the `temperatures` array looking for a warmer temperature.
    
4. Another inner loop is used to find the next warmer temperature. It continues as long as two conditions are met:
    
    * `j < len(temperatures)`: Ensure that `j` doesn't go out of bounds.
        
    * `temperatures[j] <= temperatures[i]`: Check if the temperature at day `j` is less than or equal to the temperature at day `i`.
        
5. Within the inner loop, there's a conditional check: `if res[j] <= 0`. This checks if there's already a result for day `j`. If `res[j]` is less than or equal to 0, it means we haven't found a warmer temperature yet, so we break out of the inner loop.
    
6. If the inner loop is exited without finding a warmer temperature, the code proceeds to the next step.
    
7. After exiting the inner loop, there's another conditional check: `if j < len(temperatures) && temperatures[j] > temperatures[i]`. This checks if `j` is still within bounds, and if the temperature at day `j` is indeed warmer than the temperature at day `i`.
    
8. If both conditions are met, it means a warmer temperature has been found, so the difference between `j` and `i` (i.e., `j - i`) is assigned to `res[i]`. This indicates how many days you have to wait until a warmer temperature is forecasted for day `i`.
    
9. The outer loop continues until all days in the `temperatures` array have been processed, and the `res` slice is populated with the waiting days for each day.
    
10. Finally, the function returns the `res` slice, which contains the number of days to wait for a warmer temperature for each day in the input.
    

In summary, this code efficiently calculates the number of days you have to wait for a warmer temperature for each day, taking into account the temperature forecasts for the upcoming days. It uses a nested loop and dynamic programming to optimize the process.