---
title: "Median of Two Sorted Arrays - Leetcode 4"
datePublished: Sun Jan 07 2024 14:56:36 GMT+0000 (Coordinated Universal Time)
cuid: clr3ma8if00000al1668khiym
slug: leetcode-0004
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704639341069/bb45a8e3-bbd5-4be0-8364-dd9c28768ebf.jpeg
tags: go, leetcode

---

# Problem - [Leetcode](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.

**Example 1:**

```go
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

**Example 2:**

```go
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

**Constraints:**

* `nums1.length == m`
    
* `nums2.length == n`
    
* `0 <= m <= 1000`
    
* `0 <= n <= 1000`
    
* `1 <= m + n <= 2000`
    
* `-10<sup>6</sup> <= nums1[i], nums2[i] <= 10<sup>6</sup>`
    

# Solution in Golang

```go
func findMedianSortedArrays(nums1 []int, nums2 []int) float64 {
	A, B := nums1, nums2
	total := len(nums1) + len(nums2)
	half := (total + 1) / 2

	var Aleft, Aright float64
	var Bleft, Bright float64

	if len(B) < len(A) {
		A, B = B, A
	}

	l, r := 0, len(A)-1
	for {
		i := (l + r) >> 1 // A
		j := half - i - 2 // B

		if i >= 0 {
			Aleft = float64(A[i])
		} else {
			Aleft = math.Inf(-1)
		}

		if (i + 1) < len(A) {
			Aright = float64(A[i+1])
		} else {
			Aright = math.Inf(1)
		}

		if j >= 0 {
			Bleft = float64(B[j])
		} else {
			Bleft = math.Inf(-1)
		}

		if (j + 1) < len(B) {
			Bright = float64(B[j+1])
		} else {
			Bright = math.Inf(1)
		}

		// partition is correct
		if Aleft <= Bright && Bleft <= Aright {
			// odd
			if total%2 == 1 {
				return max(Aleft, Bleft)
			}
			// even
			return (max(Aleft, Bleft) + min(Aright, Bright)) / 2
		} else if Aleft > Bright {
			r = i - 1
		} else {
			l = i + 1
		}
	}
}

func max(a, b float64) float64 {
	if a > b {
		return a
	}
	return b
}

func min(a, b float64) float64 {
	if a < b {
		return a
	}
	return b
}
```

This Go code implements the median of two sorted arrays algorithm. The goal is to find the median value of the combined sorted arrays `nums1` and `nums2`. The algorithm uses a binary search approach to efficiently partition the arrays.

Here's a breakdown of the code:

1. **Variable Initialization:**
    
    * `A` and `B` are assigned the input arrays `nums1` and `nums2`.
        
    * `total` represents the total number of elements in both arrays.
        
    * `half` is calculated as the middle index of the combined arrays.
        
2. **Partitioning and Binary Search:**
    
    * If the length of array `B` is less than `A`, swap them.
        
    * Initialize left (`l`) and right (`r`) pointers for array `A`.
        
    * Inside the binary search loop:
        
        * Calculate indices `i` for array `A` and `j` for array `B`.
            
        * Update variables (`Aleft`, `Aright`, `Bleft`, `Bright`) to store values around the partition.
            
        * Check if the partition is correct. If so, determine the median based on whether the total number of elements is odd or even.
            
        * Adjust the pointers based on the values at the current partition.
            
3. **Helper Functions:**
    
    * `max` returns the maximum of two given float64 values.
        
    * `min` returns the minimum of two given float64 values.
        

The core logic involves adjusting the partition of the arrays (`A` and `B`) until the correct position is found where elements on the left side are smaller or equal to elements on the right side. The median is then calculated based on this partition. The use of `math.Inf` represents positive and negative infinity for comparison purposes.