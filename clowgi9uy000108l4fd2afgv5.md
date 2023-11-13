---
title: "Find Minimum in Rotated Sorted Array - Leetcode 153"
seoTitle: "How to to Solve Find Minimum in Rotated Sorted Array  Leetcode 153 ?"
seoDescription: "Optimize your Go code with this snippet for finding the minimum element in sorted and rotated arrays. Efficient binary search tailored for seamless naviga.."
datePublished: Mon Nov 13 2023 05:21:06 GMT+0000 (Coordinated Universal Time)
cuid: clowgi9uy000108l4fd2afgv5
slug: leetcode-0153
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699852665150/cb401129-ecf9-44be-aca8-c193ac7dc547.jpeg
tags: go, leetcode

---

# Problem - Leetcode

Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

* `[4,5,6,7,0,1,2]` if it was rotated `4` times.
    
* `[0,1,2,4,5,6,7]` if it was rotated `7` times.
    

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return *the minimum element of this array*.

You must write an algorithm that runs in `O(log n) time.`

**Example 1:**

```plaintext
Input: nums = [3,4,5,1,2]
Output: 1
Explanation: The original array was [1,2,3,4,5] rotated 3 times.
```

**Example 2:**

```plaintext
Input: nums = [4,5,6,7,0,1,2]
Output: 0
Explanation: The original array was [0,1,2,4,5,6,7] and it was rotated 4 times.
```

**Example 3:**

```plaintext
Input: nums = [11,13,15,17]
Output: 11
Explanation: The original array was [11,13,15,17] and it was rotated 4 times. 
```

**Constraints:**

* `n == nums.length`
    
* `1 <= n <= 5000`
    
* `-5000 <= nums[i] <= 5000`
    
* All the integers of `nums` are **unique**.
    
* `nums` is sorted and rotated between `1` and `n` times.
    

# Solution in Golang

```go
func findMin(nums []int) int {
	res := nums[0]
	left, right := 0, len(nums)-1
	for left <= right {
		mid := (left + right) / 2
		if nums[mid] >= nums[0] {
			left = mid + 1
		} else {
			if nums[mid] < res {
				res = nums[mid]
			}
			right = mid - 1
		}
	}
	return res
}
```

This Go code defines a function `findMin` that takes a sorted and rotated array of integers `nums` as input and returns the minimum element in the array. The array is sorted but may have been rotated, meaning elements have been moved to the left or right.

Let's break down the code step by step:

1. `res := nums[0]`: Initializes the result variable `res` with the first element of the array. This assumes that the array is not empty.
    
2. `left, right := 0, len(nums)-1`: Initializes two pointers, `left` and `right`, which represent the range of elements currently being considered. `left` starts at the beginning of the array, and `right` starts at the end.
    
3. `for left <= right {`: Initiates a loop that continues as long as the `left` pointer is less than or equal to the `right` pointer.
    
4. `mid := (left + right) / 2`: Calculates the middle index of the current range.
    
5. `if nums[mid] >= nums[0] {`: Checks if the middle element is greater than or equal to the first element of the array. This condition is used to determine whether the rotation point is on the right side of the array.
    
    * If true, it means the minimum element is on the right side, so the `left` pointer is updated to `mid + 1`.
        
    * If false, it means the rotation point, and consequently, the minimum element, is on the left side or at the current position. In this case, it goes to the `else` block.
        
6. `if nums[mid] < res {`: Checks if the current element at the middle index is less than the current minimum (`res`).
    
    * If true, it updates the minimum (`res`) to the value at the middle index.
        
7. `right = mid - 1`: Adjusts the `right` pointer to continue searching on the left side of the array.
    
8. The loop continues until the `left` pointer exceeds the `right` pointer.
    
9. `return res`: Returns the minimum element found during the search.
    

In summary, this code efficiently finds the minimum element in a sorted and rotated array using a binary search approach. The algorithm exploits the sorted nature of the array and adapts the search based on the comparison between the middle element and the first element of the array.