---
title: "Top K Frequent Elements - Leetcode 347"
datePublished: Fri Aug 11 2023 17:03:00 GMT+0000 (Coordinated Universal Time)
cuid: cll6u6uzw000309l89o9w2ifu
slug: leetcode-0347
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691773220532/49618a55-4eb5-4cca-a5fe-9763e4e871ad.jpeg
tags: golang, leetcode, hashtables

---

# Problem - Leetcode

Given an integer array `nums` and an integer `k`, return *the* `k` *most frequent elements*. You may return the answer in **any order**.

**Example 1:**

```bash
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2:**

```bash
Input: nums = [1], k = 1
Output: [1]
```

**Constraints:**

* `1 <= nums.length <= 10<sup>5</sup>`
    
* `-10<sup>4</sup> <= nums[i] <= 10<sup>4</sup>`
    
* `k` is in the range `[1, the number of unique elements in the array]`.
    
* It is **guaranteed** that the answer is **unique**.
    

**Follow up:** Your algorithm's time complexity must be better than `O(n log n)`, where n is the array's size.

# Answer-1 in Golang

```go
func topKFrequent(nums []int, k int) []int {
    countMap := map[int]int{}
	for _, num := range nums {
		if count, ok := countMap[num]; ok {
			countMap[num] = count + 1
		} else {
			countMap[num] = 1
		}
	}

	countSlice := make([][]int, len(nums)+1)
	for num, count := range countMap {
		countSlice[count] = append(countSlice[count], num)
	}

	res := []int{}
	for i := len(countSlice) - 1; i > 0; i-- {
		res = append(res, countSlice[i]...)
		if len(res) == k {
			return res
		}
	}
	return res
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692028012474/2440db5f-c9d0-4280-9662-3d5095050221.png align="center")

This code defines a Go function called `topKFrequent` takes a slice of integer `nums` and an integer `k` as its parameters. The goal of this function is to find the `k` most frequent numbers from the input slice and return them in an output slice.

Here's how the code works:

1. `countMap := map[int]int{}`
    
    * This initializes an empty map called `countMap`. The keys of this map will be the unique numbers from the input slice, and the values will be the frequency (count) of each number.
        
2. Loop through `nums` to populate `countMap`:
    
    * The loop iterates through each number `num` in the input slice `nums`.
        
    * If `num` is already a key in `countMap`, it increments the count by 1.
        
    * If `num` is not a key in `countMap`, it adds `num` to the map with a count of 1.
        
3. `countSlice := make([][]int, len(nums)+1)`
    
    * This creates a 2D slice called `countSlice`. The outer slice will store lists of numbers grouped by their frequency. The inner slices will store the actual numbers.
        
4. Loop through `countMap` to populate `countSlice`:
    
    * The loop iterates through each key-value pair in `countMap`.
        
    * It appends the number (`num`) to the inner slice corresponding to its frequency (`count`) in `countSlice`.
        
5. Retrieve the `k` most frequent numbers:
    
    * The code initializes an empty result slice called `res`.
        
6. Iterate through `countSlice` in reverse order:
    
    * Starting from the highest possible frequency (length of `countSlice` - 1), it iterates in reverse.
        
    * It appends the numbers in the current frequency group to the result slice `res`.
        
    * If the length of `res` becomes equal to or greater than `k`, it means the required `k` most frequent numbers have been found, so the function returns `res`.
        
7. If the loop completes without finding `k` most frequent numbers:
    
    * If the loop completes without returning, it means the total number of unique numbers is less than `k`. In this case, it just returns the `res` slice.
        

In summary, this code calculates the frequency of each number in the input slice, groups the numbers based on their frequency, and returns the `k` most frequent numbers. The approach is based on using a frequency map and a frequency-based grouping in a 2D slice.

# Answer-2 Top Runtime in Golang

```go
import (
	"math"
	"sort"
)

func topKFrequent(nums []int, k int) []int {
	n := len(nums)
	if n < 2 {
		return nums
	}

	min, max := math.MaxInt32, math.MinInt32

	for _, val := range nums {
		if min > val {
			min = val
		}
		if max < val {
			max = val
		}
	}
	numRange := max - min

	//[counter, index-to-next]
	allCounters := make([][2]int, numRange+2)
	firstValue := nums[0]
	prevValue := firstValue - min +1

	diffCount := 1

	allCounters[prevValue][0] = 1
	allCounters[prevValue][1] = -1

	for _, val := range nums[1:] {
		realVal := val - min + 1

		allCounters[realVal][0] += 1

		if allCounters[realVal][1] == 0 {
			diffCount++
			allCounters[realVal][1] = prevValue
			prevValue = realVal
		}
	}

	allPairs := make([][2]int, diffCount)
	//fmt.Printf("#count: %v\n", diffCount)

	idx := 0
	for diffCount > 0 {
		val := prevValue + min - 1
		allPairs[idx][0] = allCounters[prevValue][0]
		allPairs[idx][1] = val
		prevValue = allCounters[prevValue][1]
		idx++
		diffCount--
	}

	sort.Slice(allPairs, func(i, j int) bool {
		return allPairs[i][0] > allPairs[j][0]
	})

	res := make([]int, k)
	idx = 0
	for idx < k {
		res[idx] = allPairs[idx][1]
		idx++
	}

	return res
}
```

This code defines a function `topKFrequent` that takes an array of integers `nums` and an integer `k` as input and returns an array containing the top K most frequent elements in the input array. Let's break down the code step by step:

1. The `import` statements: The code imports the necessary packages `math` and `sort` for mathematical operations and sorting, respectively.
    
2. Function `topKFrequent`: This function calculates the top K most frequent elements in the `nums` array.
    
3. Calculating the length of the input array: The variable `n` stores the length of the `nums` array.
    
4. Handling edge cases: If the length of the array is less than 2, the function returns the original array as there won't be any "top K frequent" elements.
    
5. Finding the minimum and maximum values in the array: This loop iterates through the `nums` array and finds the minimum (`min`) and maximum (`max`) values.
    
6. Calculating the range of values: The variable `numRange` calculates the range of values in the array by subtracting the minimum from the maximum value.
    
7. Initializing an array for counters and indices: The `allCounters` array is created to store two values for each element: its frequency count and the index of the next element with the same frequency.
    
8. Initializing variables:
    
    * `firstValue` holds the value of the first element in the array.
        
    * `prevValue` is initialized with the adjusted value of the first element based on the minimum value.
        
    * `diffCount` keeps track of the number of unique frequencies encountered.
        
9. Storing frequency and index information:
    
    * The frequency of the first element is set to 1 in `allCounters`.
        
    * The index of the next element with the same frequency is set to -1.
        
10. Iterating through the array to count frequencies and indices:
    

* This loop iterates through the `nums` array starting from the second element.
    
* It adjusts the current value based on the minimum value and stores it as `realVal`.
    
* The frequency count of `realVal` is incremented in `allCounters`.
    
* If the index of the next element with the same frequency is 0, it means this is a new frequency. In that case, `diffCount` is incremented, and the index is updated.
    

1. Creating an array of frequency-value pairs:
    

* An array `allPairs` is created to store the frequency-value pairs for the unique frequencies encountered.
    

1. Populating the `allPairs` array:
    

* This loop iterates until `diffCount` becomes 0.
    
* The original value is calculated by adding `min - 1` to the adjusted value.
    
* Frequency and value are stored in `allPairs`, and the next index is updated.
    

1. Sorting the pairs by frequency: The `allPairs` array is sorted in descending order based on frequency.
    
2. Extracting the top K frequent elements:
    

* An array `res` is created to store the final result.
    
* The loop extracts the top K elements from `allPairs` and stores their values in `res`.
    

1. Returning the result: The function returns the `res` array containing the top K frequent elements in descending order of frequency.
    

This code implements a more complex algorithm to solve the problem of finding the top K most frequent elements by managing indices and frequencies directly.

# Answer-3 Top Memory in Golang

```go
func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

type Pair struct {
	fr int
	sc int
}

func topKFrequent(nums []int, k int) []int {
	mn, mx := nums[0], nums[0]
	for _, v := range nums {
		mn = min(mn, v)
		mx = max(mx, v)
	}
	counter := make([]Pair, mx-mn+1)
	shift := mn
	for _, v := range nums {
		counter[v-shift].fr += 1
		counter[v-shift].sc = v
	}

	sort.Slice(counter, func(i, j int) bool {
		return counter[i].fr > counter[j].fr
	})
	ans := make([]int, k)
	for i := 0; i < k; i++ {
		ans[i] = counter[i].sc
	}
	
	return ans
}
```

This code defines a function `topKFrequent` that takes an array of integers `nums` and an integer `k` as input and returns an array containing the top K most frequent elements in the input array. Let's break down the code step by step:

1. **Function Definitions for max and min:**
    
    * Two utility functions `max` and `min` are defined. They return the maximum and minimum of two integer values, respectively.
        
2. **Defining a Pair Struct:**
    
    * A custom data structure `Pair` is defined to hold two integer values, `fr` (frequency) and `sc` (score/value). This will be used to store frequency-score pairs.
        
3. **Function** `topKFrequent`:
    
    * This function calculates the top K most frequent elements in the `nums` array.
        
4. **Finding the Minimum and Maximum Values in the Array:**
    
    * The variables `mn` and `mx` are initialized with the first element of the `nums` array.
        
    * A loop iterates through the `nums` array and updates `mn` and `mx` to find the minimum and maximum values.
        
5. **Creating a Counter Array:**
    
    * An array named `counter` of type `Pair` is created to store frequency-score pairs.
        
    * The variable `shift` is set to `mn`. This will be used to adjust the index in the `counter` array so that the minimum value corresponds to index 0.
        
6. **Populating the Counter Array:**
    
    * Another loop iterates through the `nums` array.
        
    * The frequency of the element `v` is incremented in the `counter` array at the index `v - shift`. The corresponding score `v` is also stored.
        
7. **Sorting the Counter Array:**
    
    * The `counter` array is sorted in descending order based on frequency. The `sort.Slice` function is used with a custom comparison function that compares the frequencies of two `Pair` objects.
        
8. **Extracting the Top K Frequent Elements:**
    
    * An array `ans` is created to store the final result.
        
    * A loop iterates `k` times.
        
    * The score of the `i`\-th element in the sorted `counter` array is assigned to the `i`\-th element of the `ans` array.
        
9. **Returning the Result:**
    
    * The function returns the `ans` array containing the top K frequent elements.
        

In summary, this code calculates the frequency of each element in the input array and stores the frequencies along with the corresponding values in a custom `Pair` structure. Then, it sorts the pairs based on frequency and extracts the top K elements by copying their values into the result array. This approach optimizes memory usage and avoids creating a separate map to store frequencies.