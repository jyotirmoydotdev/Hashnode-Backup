---
title: "Top K Frequent Elements - Leetcode 347"
datePublished: Fri Aug 11 2023 17:03:00 GMT+0000 (Coordinated Universal Time)
cuid: cll6u6uzw000309l89o9w2ifu
slug: top-k-frequent-elements-leetcode-347
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691773220532/49618a55-4eb5-4cca-a5fe-9763e4e871ad.jpeg
tags: golang, leetcode, hashtables

---

# Problem

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

# Answer in Golang

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