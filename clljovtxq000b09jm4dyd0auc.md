---
title: "Container With Most Water - Leetcode 11"
datePublished: Sun Aug 20 2023 16:55:28 GMT+0000 (Coordinated Universal Time)
cuid: clljovtxq000b09jm4dyd0auc
slug: leetcode-0011
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692550468142/cd803703-ea47-4d62-b049-6bff6f7dc607.jpeg
tags: golang, leetcode

---

# Problem - Leetcode

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i<sup>th</sup>` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return *the maximum amount of water a container can store*.

**Notice** that you may not slant the container.

 **Example 1:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692548716146/d17444b1-7fcb-4978-a822-8f707896e1ec.jpeg align="center")

```bash
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
```

**Example 2:**

```bash
Input: height = [1,1]
Output: 1
```

**Constraints:**

* `n == height.length`
    
* `2 <= n <= 10<sup>5</sup>`
    
* `0 <= height[i] <= 10<sup>4</sup>`
    

# Answer-1 in Golang

```go
func maxArea(height []int) int {
	left, right := 0, (len(height) - 1)
	result := 0

	for left < right {
		area := min(height[left], height[right]) * (right - left)
		if result < area {
			result = area
		}
		if height[left] > height[right] {
			right--
		} else {
			left++
		}
	}
	return result
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

The code implements a solution to the "Container With Most Water" problem using a two-pointer approach. This problem involves finding the maximum area that can be formed by choosing two lines on a coordinate plane and a vertical line drawn between them. The goal is to determine the maximum area that can be enclosed by these lines and the x-axis.

Here's a detailed breakdown of the code:

1. `maxArea` function: This is the main function that calculates the maximum area for the given array of heights.
    
2. `left` and `right` pointers: These pointers are initialized to the start and end of the `height` array, respectively. They will be used to represent the two lines forming the "container" whose area we want to maximize.
    
3. `result` variable: This variable is used to store the maximum area encountered during the process. It's initially set to 0.
    
4. `for` loop: The loop runs while the `left` pointer is less than the `right` pointer. This loop iterates through different combinations of lines to calculate the maximum area.
    
5. `area` calculation: The area is calculated using the `min` function to find the minimum height between the lines represented by `height[left]` and `height[right]`. This height is then multiplied by the width, which is the difference between `right` and `left`. The formula used is: `area = min(height[left], height[right]) * (right - left)`.
    
6. Comparing and updating `result`: The calculated `area` is compared with the current value of `result`. If the calculated area is greater, it becomes the new `result` value, storing the maximum area encountered so far.
    
7. Pointer movement: Depending on the heights of the lines at positions `left` and `right`, either the `left` pointer is moved to the right or the `right` pointer is moved to the left. This movement is done to explore different combinations of lines and find the optimal arrangement that maximizes the area.
    
8. `min` function: This function takes two integers as arguments and returns the minimum of the two.
    
9. Returning the result: Once the `left` pointer is no longer less than the `right` pointer, the loop exits, and the function returns the `result`, which represents the maximum area that can be formed by choosing two lines from the `height` array.
    

In essence, the code uses a two-pointer approach to iteratively consider different combinations of lines and calculate the areas formed by them, eventually finding the maximum area possible. The algorithm optimizes the search by moving the pointers strategically based on the heights of the lines being considered.