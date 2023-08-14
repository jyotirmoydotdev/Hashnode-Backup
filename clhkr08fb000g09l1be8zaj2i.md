---
title: "Contains Duplicate - Leetcode 217"
datePublished: Tue Aug 08 2023 15:26:07 GMT+0000 (Coordinated Universal Time)
cuid: clhkr08fb000g09l1be8zaj2i
slug: leetcode-0217
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691508333960/b8466716-db45-4055-a6b6-74bacc77a99b.jpeg
tags: cpp, sorting, array, hash-table, leetcode

---

# Problem - Leetcode

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

```go
Input: nums = [1,2,3,1]
Output: true
```

**Example 2:**

```go
Input: nums = [1,2,3,4]
Output: false
```

**Example 3:**

```go
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

**Constraints:**

* `1 <= nums.length <= 10<sup>5</sup>`
    
* `-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>`
    

# Answer-1 Top Runtime in Golang

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

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692026596859/b8b25014-0c82-4c7c-8997-64eda2a485fe.png align="center")

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

# Answer-2 Top Memory in Golang

```go
import "sort"
func containsDuplicate(nums []int) bool {
    sort.Slice(nums, func(i, j int) bool{
        return nums[i] < nums[j]
    })
    for i := 1; i < len(nums); i++ {
        if nums[i] == nums[i - 1] {
            return true
        }
    }
    return false
}
```

This code defines a function called `containsDuplicate` that takes a slice of integers (`[]int`) named `nums` as its parameter and returns a boolean value (`true` or `false`). The purpose of this function is to determine whether the given slice contains any duplicate integers.

Let's break down the code step by step:

1. The `import "sort"` statement at the beginning of the code indicates that the built-in `sort` package from Go's standard library is being imported. This package provides sorting functionalities that will be used later in the code.
    
2. The `func containsDuplicate(nums []int) bool` line defines the function `containsDuplicate` that takes a single parameter, `nums`, which is a slice of integers.
    
3. Inside the function, `sort.Slice(nums, func(i, j int) bool {...}` sorts the `nums` slice in ascending order using the `sort.Slice` function. The second argument to `sort.Slice` is an anonymous function (also known as a closure) that defines how the sorting should be performed. The function takes two indices `i` and `j`, and it compares the values at those indices in the `nums` slice. If the value at index `i` is less than the value at index `j`, the function returns `true`, indicating that the values should be swapped during sorting.
    
4. After sorting the `nums` slice, a loop is started using the `for` statement: `for i := 1; i < len(nums); i++ {...}`. The loop iterates through the sorted `nums` slice, starting from index 1 and going up to the length of the slice minus one.
    
5. Inside the loop, the code checks if the current element at index `i` is equal to the previous element at index `i - 1`. If they are equal, it means a duplicate has been found, and the function immediately returns `true`.
    
6. If the loop completes without finding any duplicates, the function returns `false` to indicate that no duplicates were found in the `nums` slice.
    

In summary, this code sorts the given slice of integers and then iterates through the sorted slice, checking for consecutive elements that are equal. If any duplicates are found, the function returns `true`; otherwise, it returns `false`. This approach leverages the sorting functionality to efficiently identify duplicate elements in the input slice.