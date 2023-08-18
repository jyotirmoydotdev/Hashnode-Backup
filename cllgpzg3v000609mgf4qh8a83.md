---
title: "3Sum - Leetcode 15"
datePublished: Fri Aug 18 2023 15:02:58 GMT+0000 (Coordinated Universal Time)
cuid: cllgpzg3v000609mgf4qh8a83
slug: leetcode-0015
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692370890657/535c1d11-4244-43b5-8809-6a14de5480db.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692370937869/06ba8d6f-f63e-40b5-b914-52949e871678.jpeg
tags: golang, leetcode

---

# Problem - Leetcode

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

```go
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```

**Example 2:**

```go
Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.
```

**Example 3:**

```go
Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
```

**Constraints:**

* `3 <= nums.length <= 3000`
    
* `-10<sup>5</sup> <= nums[i] <= 10<sup>5</sup>`
    

# Answer-1 in Golang

```go
func threeSum(nums []int) [][]int {
	quickSort(nums) //NOTE:  we can also use sort.Ints(nums)
	var result [][]int
	for num1 := 0; num1 < len(nums)-2; num1++ {
		if num1 > 0 && nums[num1] == nums[num1-1] {
			continue
		}
		num2 := num1 + 1
		num3 := len(nums) - 1
		for num2 < num3 {
			sum := nums[num2] + nums[num3] + nums[num1]
			if sum == 0 {
				result = append(result, []int{nums[num1], nums[num2], nums[num3]})
				num3--
				for num2 < num3 && nums[num3] == nums[num3+1] {
					num3--
				}
			} else if sum > 0 {
				num3--
			} else {
				num2++
			}
		}
	}
	return result
}
func quickSort(arr []int) {
	if len(arr) <= 1 {
		return
	}

	pivotIndex := len(arr) / 2
	pivot := arr[pivotIndex]

	left := make([]int, 0)
	right := make([]int, 0)

	for i, num := range arr {
		if i == pivotIndex {
			continue
		}

		if num <= pivot {
			left = append(left, num)
		} else {
			right = append(right, num)
		}
	}

	quickSort(left)
	quickSort(right)

	copy(arr, append(append(left, pivot), right...))
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692369663917/fb65762c-b524-4986-a49b-d5b2230aba57.png align="center")

The code is an implementation of the "Three Sum" problem, which is a classic problem in computer science and algorithms. The problem is defined as follows: Given an array of integers, find all unique triplets (sets of three numbers) in the array that add up to zero.

Let's break down the code step by step:

1. `func threeSum(nums []int) [][]int`: This is the main function that takes an array of integers as input and returns a 2D slice containing all the unique triplets that sum up to zero.
    
2. `quickSort(nums)`: This line sorts the input array `nums` using the `quickSort` function before processing it. The quick sort algorithm recursively divides the array into subarrays and rearranges them in a way that elements less than the pivot come before it, and elements greater than the pivot come after it.
    
3. `var result [][]int`: This declares an empty 2D slice called `result` to store the triplets that satisfy the condition.
    
4. The outer loop (`for num1 := 0; num1 < len(nums)-2; num1++`) iterates over the elements of the sorted array up to the third-to-last element. It's used to pick the first number of the triplet.
    
    * The condition `if num1 > 0 && nums[num1] == nums[num1-1]` is used to skip duplicate values. If the current number is the same as the previous one, it continues to the next iteration of the loop.
        
5. Inside the outer loop, there's an inner loop (`for num2, num3`) that scans the remaining elements from both ends of the array towards the middle to find pairs of numbers that sum up to the negative of the current `num1`.
    
    * `sum := nums[num2] + nums[num3] + nums[num1]` calculates the sum of the three numbers.
        
    * If `sum` is equal to zero, a valid triplet is found, so it's appended to the `result` slice. The pointers `num2` and `num3` are then adjusted to find more potential triplets.
        
    * If `sum` is greater than zero, the `num3` pointer is moved to the left to decrease the sum.
        
    * If `sum` is less than zero, the `num2` pointer is moved to the right to increase the sum.
        
6. Finally, the function returns the `result` slice containing all the unique triplets that satisfy the condition.
    
7. The `quickSort` function implements the quick sort algorithm to sort an input array by recursively dividing it into smaller subarrays and sorting them.
    

Overall, this code efficiently solves the "Three Sum" problem by employing a two-pointer approach along with sorting the input array to facilitate finding the unique triplets that sum up to zero.

The time complexity of the code is dominated by two main factors: the sorting step and the nested loops for finding the three sum triplets.

1. Sorting: The `quickSort` function sorts the input array before the main algorithm is executed. Quick sort has an average time complexity of O(n log n) and a worst-case time complexity of O(n^2) when the pivot choice is consistently bad. The worst-case time complexity is less likely to occur in practice due to randomization or careful pivot selection.
    
2. Finding Triplets: The main algorithm involves nested loops. The outer loop iterates over `n` elements (where `n` is the length of the input array). For each outer loop iteration, the inner loop scans the remaining elements, which at most is again `n` iterations. However, since the pointers move towards each other, the average time complexity of the inner loop is closer to O(n/2).
    

Combining these factors, the overall time complexity of the given code is dominated by the sorting step (O(n log n)) and the nested loops (O(n^2)), which makes the overall time complexity O(n^2). This is the worst-case scenario for the given implementation. In practice, due to the early stopping mechanisms and the benefits of quick sort, the actual performance may be better than this worst-case estimation.