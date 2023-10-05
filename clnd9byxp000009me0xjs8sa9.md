---
title: "Binary Search - Leetcode 704"
datePublished: Thu Oct 05 2023 14:12:55 GMT+0000 (Coordinated Universal Time)
cuid: clnd9byxp000009me0xjs8sa9
slug: leetcode-0704
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696515043016/9cf738b2-a951-4a08-aade-0863b86bd315.jpeg
tags: programming, leetcode

---

# Problem - Leetcode

Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```

**Example 2:**

```
Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
```

**Constraints:**

* `1 <= nums.length <= 10<sup>4</sup>`
    
* `-10<sup>4</sup> < nums[i], target < 10<sup>4</sup>`
    
* All the integers in `nums` are **unique**.
    
* `nums` is sorted in ascending order.
    
* `30 <= temperatures[i] <= 100`
    

# Solution in Golang

```go
func search(nums []int, target int) int {
    left := 0
    right := len(nums)-1
    for left<=right{
        mid := (left+right)/2
        if nums[mid]==target{
            return mid
        }else if nums[mid]<target{
            left = mid +1
        }else {
            right = mid -1
        }
    }
    return -1
}
```

This is a Go programming language function called `search` that performs a binary search to find a target integer within a sorted array of integers. Let me break down the code step by step:

1. `func search(nums []int, target int) int {`: This line defines a function named `search` that takes two arguments:
    
    * `nums` is a slice of integers, representing the sorted array in which we want to search for the `target` value.
        
    * `target` is the integer we want to find in the `nums` array.
        
    * The function returns an integer, which is the index of the `target` in the array if found, or -1 if it's not found.
        
2. `left := 0` and `right := len(nums)-1`: These lines initialize two variables `left` and `right`. `left` represents the left boundary of the current search range, initialized to the beginning of the array (index 0), and `right` represents the right boundary, initialized to the end of the array (index `len(nums)-1`).
    
3. `for left <= right {`: This starts a loop that continues as long as the `left` boundary is less than or equal to the `right` boundary. This loop is the heart of the binary search algorithm.
    
4. `mid := (left+right)/2`: Inside the loop, it calculates the middle index `mid` of the current search range by taking the average of `left` and `right`. This is where the binary search gets its name because it repeatedly divides the search range in half.
    
5. `if nums[mid] == target {`: This checks if the value at the middle index `mid` of the array `nums` is equal to the `target`. If it is, this means we've found the `target`, and the function returns `mid`, which is the index where `target` is located in the array.
    
6. `else if nums[mid] < target {`: If the value at `mid` is less than the `target`, which means the `target` must be in the right half of the current search range. So, it updates `left` to `mid + 1`, effectively narrowing the search range to the right half.
    
7. `else {`: If the value at `mid` is greater than the `target`, which means the `target` must be in the left half of the current search range. So, it updates `right` to `mid - 1`, narrowing the search range to the left half.
    
8. If the loop exits without finding the `target`, i.e., `left` becomes greater than `right`, the function returns `-1` to indicate that the `target` is not in the array.
    

In summary, this code performs an efficient binary search on a sorted array to find the index of a specific target value, and it returns that index or -1 if the target is not in the array. Binary search is efficient because it repeatedly divides the search range in half, reducing the number of comparisons needed to find the target in a sorted array.