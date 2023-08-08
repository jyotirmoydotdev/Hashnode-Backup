---
title: "Contains Duplicate - Leetcode 217"
datePublished: Tue Aug 08 2023 15:26:07 GMT+0000 (Coordinated Universal Time)
cuid: clhkr08fb000g09l1be8zaj2i
slug: contains-duplicate-leetcode-217
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691508333960/b8466716-db45-4055-a6b6-74bacc77a99b.jpeg
tags: cpp, sorting, array, hash-table, leetcode

---

# Problem

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

```plaintext
Input: nums = [1,2,3,1]
Output: true
```

```plaintext
Input: nums = [1,2,3,4]
Output: false
```

```plaintext
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

**Constraints:**

* `1 <= nums.length <= 10<sup>5</sup>`
    
* `-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>`
    

# Answer

```go
func containsDuplicate(nums []int) bool {
	nums_map := map[int]int{}
	for _, n := range nums {
		if _, ok := nums_map[n]; !ok {
			nums_map[n] = 1
		} else {
			return true
		}
	}
	return false
}
```

This code defines a function named `containsDuplicate` that takes a single argument `nums`, which is a slice of integers. The purpose of this function is to determine whether the given slice of integers contains any duplicates or not. It returns a boolean value (`true` if there are duplicates, and `false` otherwise).

Here's a step-by-step breakdown of the code:

1. The function starts by declaring an empty map named `nums_map`, which is used to keep track of the frequency of each integer in the input slice. The keys of the map are integers, and the values are integers representing the frequency of each integer in the slice.
    
2. The code then enters a loop that iterates over each element (`n`) in the input `nums` slice.
    
3. Inside the loop, the code checks whether the current integer `n` is already present in the `nums_map` by using the line:
    
    ```go
    if _, ok := nums_map[n]; !ok {
    ```
    
4. Here, `ok` is a boolean variable that indicates whether the key `n` is present in the map or not. If `n` is not present (`!ok` is true), then the code sets the frequency of `n` to `1` in the `nums_map`, indicating that this integer has been encountered once.
    
5. If the integer `n` is already present in the `nums_map`, it means that there's a duplicate. In that case, the code immediately returns `true`, indicating that duplicates have been found in the input slice.
    
6. If no duplicate has been found during the iteration, the code returns `false`, indicating that no duplicates were detected in the input slice.
    

In essence, this code uses a map to keep track of the frequency of integers in the input slice. If any integer is encountered more than once, it means there's a duplicate, and the function returns `true`. Otherwise, if no duplicates are found after iterating through the entire input slice, the function returns `false`.