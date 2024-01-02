---
title: "Search in Rotated Sorted Array - Leetcode 0033"
datePublished: Tue Jan 02 2024 16:09:38 GMT+0000 (Coordinated Universal Time)
cuid: clqwjoweb000808l30w7w5wak
slug: search-in-rotated-sorted-array-leetcode-0033
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704211729135/7b5839f9-3cee-4d2e-9d66-15c1b4406499.png
tags: go, leetcode

---

# Problem - [Leetcode](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return *the index of* `target` *if it is in* `nums`*, or* `-1` *if it is not in* `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```plaintext
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

**Example 2:**

```plaintext
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

**Example 3:**

```plaintext
Input: nums = [1], target = 0
Output: -1
```

**Constraints:**

* `1 <= nums.length <= 5000`
    
* `-10<sup>4</sup> <= nums[i] <= 10<sup>4</sup>`
    
    All values of `nums` are **unique**.
    
* `nums` is an ascending array that is possibly rotated.
    
* `-10<sup>4</sup> <= target <= 10<sup>4</sup>`
    

# Solution in Golang

```go
func search(nums []int, target int) int {
    left, right := 0, len(nums) - 1
    
    for left <= right {
        mid := (left + right) / 2
        if target == nums[mid] {
            return mid
        }
        
        // left sorted portion
        if nums[left] <= nums[mid] {
            if target > nums[mid] || target < nums[left] {
                left = mid + 1
            } else {
                right = mid - 1
            }
        // Right sorted portion
        } else {
            if target < nums[mid] || target > nums[right] {
                right = mid - 1
            } else {
                left = mid + 1
            }
        }
    }
    return -1
}
```

This is an implementation of a binary search algorithm to find the index of a target element in a rotated sorted array. The function takes two parameters: a sorted array `nums` and a target element `target`. It initializes two pointers, `left` and `right`, which represent the range of indices to search within.

The algorithm then enters a while loop, where it calculates the middle index `mid` of the current range. If the target is equal to the element at the middle index, it returns the index.

The interesting part comes when dealing with the rotated sorted array. It checks whether the left portion or the right portion of the array is sorted. If the left portion is sorted, it checks whether the target lies within that sorted range. If it does, the search continues in the left portion; otherwise, it shifts the search to the right portion. Similarly, if the right portion is sorted, it checks whether the target lies within that range and adjusts the search accordingly.

This approach allows the algorithm to handle rotated sorted arrays efficiently, maintaining the logarithmic time complexity of the standard binary search.