---
title: "Sliding Window Maximum - Leetcode 239"
datePublished: Sun Sep 03 2023 12:50:58 GMT+0000 (Coordinated Universal Time)
cuid: clm3gbc0m000609md8j8pbym8
slug: leetcode-0239
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693745378184/41d10d91-8356-430a-a5c9-f7bee5cefca1.jpeg
tags: go, leetcode

---

# Problem - Leetcode

You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.

Return *the max sliding window*. 

**Example 1:**

```go
Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
Output: [3,3,5,5,6,7]
Explanation: 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

**Example 2:**

```go
Input: nums = [1], k = 1
Output: [1]
```

**Constraints:**

* `1 <= nums.length <= 10<sup>5</sup>`
    
* `-10<sup>4</sup> <= nums[i] <= 10<sup>4</sup>`
    
* `1 <= k <= nums.length`
    

# Solution in Golang

```go
func maxSlidingWindow(nums []int, k int) []int {
	output := []int{}
	q := make([]int, 0)
	l, r := 0, 0
	for r < len(nums) {
		for len(q) != 0 && nums[q[len(q)-1]] < nums[r] {
			q = q[:len(q)-1]
		}
		q = append(q, r)
		if l > q[0] {
			q = q[1:]
		}
		if (r + 1) >= k {
			output = append(output, nums[q[0]])
			l++
		}
		r++
	}
	return output
} 
```

This code defines a function `maxSlidingWindow` that takes two parameters: a slice of integers `nums` and an integer `k`. The goal of this function is to find the maximum element in a sliding window of size `k` as it moves from left to right through the `nums` slice and return the maximum values in a new slice.

Here's a step-by-step explanation of how the code works:

1. Initialize `output` as an empty slice of integers to store the maximum values found in the sliding window.
    
2. Create an empty slice `q` to act as a deque (double-ended queue) for storing indices of elements in the `nums` slice.
    
3. Initialize two pointers `l` and `r` to 0. `l` represents the left end of the sliding window, and `r` represents the right end of the sliding window.
    
4. Start a `for` loop that continues until the right pointer `r` reaches the end of the `nums` slice.
    
5. Inside the loop, there is another `for` loop that runs while the deque `q` is not empty and the element at the last index in `q` (i.e., `nums[q[len(q)-1]]`) is less than the current element `nums[r]`. This inner loop removes elements from the back of the deque `q` until the condition is met, effectively maintaining a deque of decreasing elements.
    
6. After the inner loop, the current index `r` is appended to the deque `q`. This is done because it is possible that the maximum element for the current window might be the element at index `r`.
    
7. Check if the left pointer `l` is greater than the index stored at the front of the deque `q`. If it is, this means that the front element in `q` is outside the current window, so we remove it from the front of the deque.
    
8. Check if the size of the current sliding window (i.e., `r+1`) is greater than or equal to `k`. If it is, this means that the window has reached the desired size of `k`, and we can add the maximum element in the window (which is `nums[q[0]]`, where `q[0]` stores the index of the maximum element) to the `output` slice. Then, increment the left pointer `l`.
    
9. Increment the right pointer `r` to move the sliding window one step to the right.
    
10. Repeat steps 4 to 9 until the right pointer `r` reaches the end of the `nums` slice.
    
11. Finally, return the `output` slice, which contains the maximum values for each sliding window of size `k`.
    

In summary, this code efficiently finds the maximum values in a sliding window of size `k` as it moves through the input slice `nums` using a deque data structure to optimize the process.