---
title: "Two Sum - Leetcode 1"
datePublished: Tue Aug 08 2023 14:37:38 GMT+0000 (Coordinated Universal Time)
cuid: cld3pgnm3000209mldhk29u5q
slug: leetcode-0001
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691501724548/0e8de6ca-3833-4704-9201-9216d2fe69d0.jpeg
tags: array, hash-table, leetcode

---

# Problem - Leetcode

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to* `target`.

You may assume that each input would have ***exactly* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

**Example 1:**

```go
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```go
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```go
Input: nums = [3,3], target = 6
Output: [0,1]
```

**Constraints:**

* `2 <= nums.length <= 10<sup>4</sup>`
    
* `-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>`
    
* `-10<sup>9</sup> <= target <= 10<sup>9</sup>`
    
* **Only one valid answer exists.**
    

**Follow-up:** Can you come up with an algorithm that is less than`O(n<sup>2</sup>)` time complexity?

# Answer-1 Top Runtime in Golang

```go
func twoSum(nums []int, target int) []int {
	m := make(map[int]int)
	for i, num := range nums {
		if _, ok := m[target-num]; ok {
			fmt.Println("ok :", ok)
			return []int{m[target-num], i}
		}
		m[num] = i
	}
	return []int{}
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692024022860/ec15b05e-977a-4a28-975e-d81c5a6f8cf3.png align="center")

This code defines a function called twoSum that takes an array of integers (nums) and an integer (target) as input and returns an array of two integers. The goal of the function is to find two distinct indices in the nums array whose corresponding values sum up to the given target.

Here’s a breakdown of how the code works:

1. Initialize an empty map m to store the elements of the nums array along with their corresponding indices.
    
2. Iterate through each element in the nums array using the for loop. The loop variable i represents the index, and num represents the value at that index.
    
3. Inside the loop:
    
    * Calculate the difference target - num.
        
    * Check if the calculated difference exists as a key in the map m using the `_, ok := m[target-num]` statement.
        
    * If the difference exists as a key (ok is true), it means we have found a pair of elements whose sum equals the target. We return an array containing the indices of those elements: \[m\[target-num\], i\].
        
4. If the difference was not found in the map, add the current num as a key to the map m, with the value being the current index i.
    
5. If the loop completes without finding a valid pair, return an empty array (\[\]int{}) to indicate that no such pair was found.
    

In essence, the code utilizes a hash map to keep track of the elements encountered so far. For each element num, it checks if the difference target - num exists in the map. If it does, the function returns the indices of the two elements that sum up to the target. If not, the element is added to the map for future reference. This approach ensures that we can quickly look up elements in the map to find pairs that satisfy the sum requirement.

The time complexity of this algorithm is O(n), where “n” is the number of elements in the nums array, as we only need to iterate through the array once. The space complexity is also O(n), as the map can store up to “n” elements in the worst case.

# Answer-2 Top memory in Golang

```go
func twoSum(nums []int, target int) []int {
    for i := 0; i < len(nums); i++ {
        for j := i + 1; j < len(nums); j++ {
            sum := nums[i] + nums[j]
            if sum == target {
                return []int{i, j}
            }
        }
    }
    return []int{}
}
```

This code defines a function called `twoSum` that takes two parameters: a slice of integers named `nums` and an integer named `target`. The goal of this function is to find and return the indices of two numbers within the `nums` slice that add up to the given `target` value.

Here's a detailed breakdown of how the code works:

1. The function starts by using two nested loops to iterate over the `nums` slice. The outer loop iterates through each element at index `i`, and the inner loop iterates through each element at index `j`, where `j` is greater than `i`.
    
2. Inside the inner loop, the code calculates the sum of the elements at indices `i` and `j`, storing it in the variable `sum`.
    
3. It then checks whether the calculated `sum` is equal to the given `target`. If it is, that means the two elements at indices `i` and `j` form a valid pair whose sum is equal to the `target`.
    
4. If the sum is equal to the target, the function immediately returns a new integer slice containing the indices `i` and `j`. These indices represent the positions of the two numbers in the `nums` slice that fulfill the sum requirement.
    
5. If the loop completes without finding a valid pair that satisfies the sum requirement, the function returns an empty integer slice `[]int{}` to indicate that no such pair was found.
    

In summary, the `twoSum` function employs a brute-force approach by iterating through all possible pairs of numbers in the `nums` slice and checking if their sum equals the given `target`. If a valid pair is found, it returns their indices; otherwise, it returns an empty slice. This approach has a time complexity of O(n^2), where 'n' is the number of elements in the `nums` slice.