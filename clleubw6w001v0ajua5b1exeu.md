---
title: "Two Sum II - Input Array Is Sorted - Leetcode 167"
datePublished: Thu Aug 17 2023 07:29:04 GMT+0000 (Coordinated Universal Time)
cuid: clleubw6w001v0ajua5b1exeu
slug: leetcode-0167
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692257003894/8b988791-94c5-4a60-a900-9d8fac660027.jpeg
tags: golang, dsa, leetcode

---

# Problem - Leetcode

Given a **1-indexed** array of integers `numbers` that are already ***sorted in non-decreasing order***, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index<sub>1</sub>]` and `numbers[index<sub>2</sub>]` where `1 <= index<sub>1</sub> < index<sub>2</sub> < numbers.length`.

Return *the indices of the two numbers,* `index<sub>1</sub>` *and* `index<sub>2</sub>`*,* ***added by one*** *as an integer array* `[index<sub>1</sub>, index<sub>2</sub>]` *of length 2.*

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

**Example 1:**

```go
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
```

**Example 2:**

```go
Input: numbers = [2,3,4], target = 6
Output: [1,3]
Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].
```

**Example 3:**

```go
Input: numbers = [-1,0], target = -1
Output: [1,2]
Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
```

**Constraints:**

* `2 <= numbers.length <= 3 * 10<sup>4</sup>`
    
* `-1000 <= numbers[i] <= 1000`
    
* `numbers` are sorted in **non-decreasing order**.
    
* `-1000 <= target <= 1000`
    
* The tests are generated such that there is **exactly one solution**.
    

# Answer-1 in Golang

```go
func twoSum(numbers []int, target int) []int {
	left, right := 0, len(numbers)-1
	for left < right {
		if numbers[left]+numbers[right] < target {
			left++
		} else if numbers[left]+numbers[right] > target {
			right--
		} else {
			return []int{left + 1, right + 1}
		}
	}
	return nil
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692257204016/7fc1952a-b8ee-4875-87ae-f8d74539e268.png align="center")

This code defines a function called `twoSum` that takes in an array of integers called `numbers` and an integer `target`. The goal of the function is to find a pair of indices in the `numbers` array whose corresponding elements add up to the given `target` value. The function returns an array containing the two indices of the elements that form the desired sum.

Here's a detailed breakdown of how the code works:

1. The function `twoSum` starts by initializing two pointers: `left` pointing to the beginning of the `numbers` array (index 0), and `right` pointing to the end of the array (index `len(numbers) - 1`).
    
2. The code enters a loop that continues as long as the `left` pointer is less than the `right` pointer. This loop is designed to converge the pointers towards each other in search of a valid pair of elements.
    
3. Within the loop, the code checks whether the sum of the elements at the indices pointed to by `left` and `right` is less than, greater than, or equal to the `target`.
    
4. If the sum of the elements at the current `left` and `right` indices is less than the `target`, the `left` pointer is incremented to move towards larger values, as adding larger elements might help reach the target sum.
    
5. If the sum of the elements at the current indices is greater than the `target`, the `right` pointer is decremented to move towards smaller values, as subtracting smaller elements might help reach the target sum.
    
6. If the sum of the elements at the current indices is exactly equal to the `target`, it means the pair has been found. In this case, the function immediately returns an array containing the indices `left + 1` and `right + 1`. Adding 1 to each index compensates for the 0-based indexing in the array.
    
7. If the loop completes without finding a suitable pair of elements that add up to the target sum, the function returns `nil`, indicating that no such pair was found.
    

In essence, the code employs a two-pointer approach to efficiently search for the desired pair of elements in the `numbers` array. It moves the pointers closer together by adjusting them based on the sum of the elements at their corresponding indices. When the pointers meet, either a pair summing to the target is found or it's determined that no such pair exists in the array.