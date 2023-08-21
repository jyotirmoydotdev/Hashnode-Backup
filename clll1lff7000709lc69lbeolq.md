---
title: "Trapping Rain Water - Leetcode 42"
datePublished: Mon Aug 21 2023 15:39:04 GMT+0000 (Coordinated Universal Time)
cuid: clll1lff7000709lc69lbeolq
slug: leetcode-0042
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692632259755/37fa35af-fcb1-44bf-b9cd-2b4c05acd0e9.jpeg
tags: go, leetcode

---

# Problem - Leetcode

Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after rain.

**Example 1:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692631235765/77fd78e5-9a5c-4744-9219-473b0bf4a6e4.png align="center")

```go
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
```

**Example 2:**

```go
Input: height = [4,2,0,3,2,5]
Output: 9
```

**Constraints:**

* `n == height.length`
    
* `1 <= n <= 2 * 10<sup>4</sup>`
    
* `0 <= height[i] <= 10<sup>5</sup>`
    

# Answer-1 in Golang

```go
func trap(height []int) int {
	if height == nil {
		return 0
	}
	left, right := 0, len(height)-1
	leftMax, rightMax := height[left], height[right]
	result := 0

	for left < right {
		if leftMax < rightMax {
			left++
			leftMax = max(leftMax, height[left])
			result = result + leftMax - height[left]
		} else {
			right--
			rightMax = max(rightMax, height[right])
			result = result + rightMax - height[right]
		}
	}
	return result
}

func max(a int, b int) int {
	if a > b {
		return a
	}
	return b
}
```

This code defines a function `trap` in Go that calculates the amount of trapped rainwater between bars of varying heights represented by the `height` array. It uses a two-pointer approach to find the trapped water. Here's a detailed breakdown of the code:

1. The `trap` function takes an input array `height` which represents the heights of bars.
    
2. It checks if the input array is nil, and if so, returns 0 (since there's no trapped water if there are no bars).
    
3. Initialize two pointers `left` and `right` to the beginning and end of the `height` array, respectively.
    
4. Initialize two variables `leftMax` and `rightMax` to store the maximum height encountered on the left and right sides, both initialized to the heights of the first and last bars.
    
5. Initialize a variable `result` to store the total trapped rainwater, initially set to 0.
    
6. Enter a `for` loop while the `left` pointer is less than the `right` pointer:
    
    1. Compare `leftMax` and `rightMax` to determine which side has a smaller maximum height.
        
    2. If `leftMax` is smaller, increment the `left` pointer, update `leftMax` to the new maximum height, and add the difference between `leftMax` and the height at `height[left]` to `result`.
        
    3. If `rightMax` is smaller (or equal), decrement the `right` pointer, update `rightMax` to the new maximum height, and add the difference between `rightMax` and the height at `height[right]` to `result`.
        
7. Once the `for` loop ends (when `left` is no longer less than `right`), return the `result` variable, which contains the total trapped rainwater.
    
8. The `max` function is a utility function that takes two integers `a` and `b` and returns the maximum of the two.
    

The overall idea behind this code is to calculate the trapped rainwater by comparing the heights of the bars on the left and right sides. It iterates through the bars using the two-pointer approach and keeps track of the maximum heights encountered. By calculating the difference between the maximum height and the current height at each step, it accurately calculates the trapped rainwater.