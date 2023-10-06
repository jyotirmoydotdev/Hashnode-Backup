---
title: "Search a 2D Matrix - Leetcode 74"
datePublished: Fri Oct 06 2023 18:36:45 GMT+0000 (Coordinated Universal Time)
cuid: clney7483000109mi4pfyglz7
slug: leetcode-0074
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696617114303/cb190415-1126-4078-8795-8ceb3d381640.jpeg
tags: go, leetcode

---

# Problem - Leetcode

You are given an `m x n` integer matrix `matrix` with the following two properties:

* Each row is sorted in non-decreasing order.
    
* The first integer of each row is greater than the last integer of the previous row.
    

Given an integer `target`, return `true` *if* `target` *is in* `matrix` *or* `false` *otherwise*.

You must write a solution in `O(log(m * n))` time complexity.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696615938196/2b9ad813-8103-4ad8-909e-73bfc460677a.jpeg align="center")

```go
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
```

**Example 2:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696615983342/4e5d149f-4401-4494-9f26-a0f6d84f0221.jpeg align="center")

```go
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false
```

**Constraints:**

* `m == matrix.length`
    
* `n == matrix[i].length`
    
* `1 <= m, n <= 100`
    
* `-10<sup>4</sup> <= matrix[i][j], target <= 10<sup>4</sup>`
    

# Solution in Golang

```go
func searchMatrix(matrix [][]int, target int) bool {
	ROWS := len(matrix)
	COLUMNS := len(matrix[0])

	top := 0
	bot := ROWS - 1

	for top <= bot {
		row := (top + bot) / 2
		if target > matrix[row][len(matrix[row])-1] {
			top = row + 1
		} else if target < matrix[row][0] {
			bot = row - 1
		} else {
			break
		}
	}

	if !(top <= bot) {
		return false
	}

	row := (top + bot) / 2
	left := 0
	right := COLUMNS - 1
	for left <= right {
		middle := (left + right) / 2
		if matrix[row][middle] == target {
			return true
		} else if matrix[row][middle] < target {
			left = middle + 1
		} else {
			right = middle - 1
		}
	}
	return false

}
```

This code defines a Go function `searchMatrix` that takes a 2D matrix of integers `matrix` and an integer `target` as input and returns a boolean value indicating whether the target is present in the matrix. The function uses a binary search approach to efficiently search for the target element.

Here's a step-by-step explanation of the code:

1. Get the number of rows (`ROWS`) and columns (`COLUMNS`) in the matrix.
    
2. Initialize two pointers, `top` and `bot`, to keep track of the range of rows to search. Initially, `top` points to the first row (0), and `bot` points to the last row (ROWS - 1).
    
3. Perform a binary search on the rows of the matrix using the `top` and `bot` pointers. This loop continues until `top` is less than or equal to `bot`. Inside the loop:
    
    * Calculate the middle row as `(top + bot) / 2`.
        
    * Check if the target value is greater than the last element of the middle row (`matrix[row][len(matrix[row])-1]`). If it is, update `top` to `row + 1` because the target must be in a lower row.
        
    * If the target is less than the first element of the middle row, update `bot` to `row - 1` because the target must be in a higher row.
        
    * If neither of the above conditions is met, it means the target is within the range of the current row, so break out of the loop.
        
4. After the binary search for rows, check if `top` is still less than or equal to `bot`. If not, it means the target is not in the matrix, so return `false`.
    
5. If the target is still potentially in the matrix (based on the row search), calculate the middle row again as `(top + bot) / 2`. Initialize two more pointers, `left` and `right`, to keep track of the columns within the current row.
    
6. Perform a binary search on the columns of the current row using the `left` and `right` pointers. This loop continues until `left` is less than or equal to `right`. Inside the loop:
    
    * Calculate the middle column as `(left + right) / 2`.
        
    * Check if the element at `matrix[row][middle]` is equal to the target. If it is, return `true` because the target is found.
        
    * If the element at the middle column is less than the target, update `left` to `middle + 1` because the target must be in the right half of the row.
        
    * If the element at the middle column is greater than the target, update `right` to `middle - 1` because the target must be in the left half of the row.
        
7. If the loop for column search completes without finding the target, return `false`.
    

In summary, this code efficiently searches for a target value in a sorted 2D matrix by performing two binary searches: one to find the appropriate row where the target might exist and another to find the target within that row. If the target is found, the function returns `true`; otherwise, it returns `false`.