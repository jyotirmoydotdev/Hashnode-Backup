---
title: "Longest Consecutive Sequence - Leetcode 128"
datePublished: Mon Aug 14 2023 16:05:34 GMT+0000 (Coordinated Universal Time)
cuid: cllb2gk10000e09ju4n3k7oyv
slug: leetcode-0128
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692030744082/23afb036-ed03-4ea8-8dd6-a1fdd9e57cdd.jpeg
tags: golang, leetcode

---

# Problem - Leetcode

Given an unsorted array of integers `nums`, return *the length of the longest consecutive elements sequence.*

You must write an algorithm that runs in `O(n)` time.

 **Example 1:**

```go
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

**Example 2:**

```go
Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
```

**Constraints:**

* `0 <= nums.length <= 10<sup>5</sup>`
    
* `-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>`
    

# Answer-1 in Golang

```go
func longestConsecutive(nums []int) int {
	set := make(map[int]bool)
	for _, num := range nums {
		set[num] = true
	}
	res := 0
	for _, num := range nums {
		if set[num-1] {
			continue
		}
		sequence := 1
		temp := num + 1
		for set[temp] {
			sequence++
			temp++
		}
		if sequence > res {
			res = sequence
		}
	}
	return res
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692028715918/b063ec3d-be68-407f-9516-7911f0675257.png align="center")

This code defines a function `longestConsecutive` that takes an array of integers `nums` as input and returns the length of the longest consecutive subsequence within the array. Let's break down the code step by step:

1. **Function** `longestConsecutive`:
    
    * This function calculates the length of the longest consecutive subsequence in the input array.
        
2. **Creating a Set:**
    
    * A set (`map[int]bool`) named `set` is created to store unique integers.
        
    * The first loop iterates through the `nums` array and inserts each element into the `set` with a value of `true`. This ensures that duplicates are removed and we have a set of unique values.
        
3. **Initializing Result Variable:**
    
    * The variable `res` is initialized to store the result, which will be the length of the longest consecutive subsequence.
        
4. **Finding Longest Consecutive Subsequence:**
    
    * The second loop iterates through the `nums` array again.
        
    * For each element `num`, it checks if `num-1` is present in the `set`. If it is, this means `num` is not the starting point of a consecutive sequence, so the loop continues to the next iteration.
        
    * If `num-1` is not present in the `set`, it means `num` is the potential starting point of a consecutive sequence.
        
    * The variable `sequence` is initialized to 1, representing the length of the sequence that starts at `num`.
        
    * The variable `temp` is initialized to `num + 1`, and the loop searches for consecutive elements in the `set` by checking if `temp` exists.
        
    * While consecutive elements are found in the `set`, the `sequence` counter is incremented, and `temp` is incremented to move to the next element.
        
    * After the loop, the length of the consecutive subsequence starting at `num` is stored in the `sequence` variable.
        
5. **Updating the Result:**
    
    * If the `sequence` length is greater than the current value of `res`, the value of `res` is updated with the length of the current sequence. This ensures that the maximum sequence length is tracked.
        
6. **Returning the Result:**
    
    * After the loop completes, the function returns the value of `res`, which represents the length of the longest consecutive subsequence.
        

In summary, this code uses a set to efficiently store unique integers from the input array. Then, it iterates through the array again, checking for each element whether it's the starting point of a consecutive sequence. If it is, the code counts the length of that consecutive sequence and updates the result if a longer sequence is found. This approach has a time complexity of O(n) due to the two loops, where n is the length of the input array.

# Answer-2 Top Runtime in Golang

```go
func getMax(a, b int) int {
    if a > b {
        return a
    }
    return b
}
func longestConsecutive(nums []int) int {
    if len(nums) == 0 {
        return 0
    } 
    sort.Ints(nums)
    cur, maxVal := 1, 1
    for i := 1 ; i < len(nums) ; i ++ {
        if nums[i-1]+1 == nums[i] {
            cur++
        } else if nums[i-1] == nums[i] {
            continue
        } else {
            cur = 1
        }
        maxVal = getMax(maxVal, cur)
    }
    return maxVal
}
```

This code defines a function `longestConsecutive` that takes an array of integers `nums` as input and returns the length of the longest consecutive subsequence within the array. Let's break down the code step by step:

1. **Function Definitions for** `getMax`:
    
    * A utility function `getMax` is defined to return the maximum of two integer values.
        
2. **Function** `longestConsecutive`:
    
    * This is the main function that calculates the length of the longest consecutive subsequence in the input array.
        
3. **Handling Empty Array:**
    
    * The function first checks if the length of the `nums` array is zero. If it is, there are no elements, and the function immediately returns 0.
        
4. **Sorting the Input Array:**
    
    * The `nums` array is sorted in ascending order using the `sort.Ints` function. Sorting is performed to make consecutive elements adjacent to each other.
        
5. **Initializing Variables:**
    
    * The variables `cur` and `maxVal` are initialized to 1.
        
    * `cur` will keep track of the length of the current consecutive subsequence being processed.
        
    * `maxVal` will store the maximum length of consecutive subsequences encountered.
        
6. **Iterating Through the Sorted Array:**
    
    * A loop starts from the second element (index 1) and iterates through the `nums` array.
        
    * For each iteration, the code checks three conditions:
        
        * If the previous element (`nums[i-1]`) plus 1 is equal to the current element (`nums[i]`), it means the current element is part of a consecutive sequence. In this case, the `cur` counter is incremented.
            
        * If the previous element is equal to the current element, it means the current element is a duplicate. The loop continues to the next iteration.
            
        * If neither of the above conditions is satisfied, it means the current element breaks the consecutive sequence. The `cur` counter is reset to 1.
            
7. **Updating** `maxVal`:
    
    * After evaluating the conditions for each element, the `maxVal` is updated using the `getMax` utility function. It compares the current value of `maxVal` with the current value of `cur` and updates `maxVal` if `cur` is greater.
        
8. **Returning the Result:**
    
    * After processing all elements, the function returns the value of `maxVal`, which represents the length of the longest consecutive subsequence in the input array.
        

In summary, this code calculates the length of the longest consecutive subsequence by sorting the array and then iterating through it. It keeps track of the current consecutive sequence length and updates the maximum length encountered. The approach has a time complexity of O(n \* log n) due to the sorting step, where n is the length of the input array. The subsequent loop has a time complexity of O(n).

# Answer-3 Top Memory in Golang

```go
func longestConsecutive(nums []int) int {
	if len(nums) == 0 { return 0 }
	sort.Slice(nums, func (i, j int) bool {
		return nums[i] < nums[j]
	})
	longest := 1
	current := 1
	for i := 1; i < len(nums); i++ {
		if nums[i] == nums[i-1] + 1 {
			current++
		} else if nums[i] != nums[i -1] {
			current = 1
		}
		if current > longest {
			longest = current
		}
	}
	return longest
}
```

This code defines a function `longestConsecutive` that takes an array of integers `nums` as input and returns the length of the longest consecutive subsequence within the array. Let's break down the code step by step:

1. **Function** `longestConsecutive`:
    
    * This is the main function that calculates the length of the longest consecutive subsequence in the input array.
        
2. **Handling Empty Array:**
    
    * The function first checks if the length of the `nums` array is zero. If it is, there are no elements, and the function immediately returns 0.
        
3. **Sorting the Input Array:**
    
    * The `nums` array is sorted in ascending order using the `sort.Slice` function. Sorting is performed using a custom comparison function that returns `true` if `nums[i]` is less than `nums[j]`. Sorting is done to ensure that consecutive elements are adjacent to each other after sorting.
        
4. **Initializing Variables:**
    
    * The variables `longest` and `current` are initialized to 1.
        
        * `longest` will store the length of the longest consecutive subsequence encountered.
            
        * `current` will keep track of the length of the current consecutive subsequence being processed.
            
5. **Iterating Through the Sorted Array:**
    
    * A loop starts from the second element (index 1) and iterates through the sorted `nums` array.
        
    * For each iteration, the code checks two conditions:
        
        * If the current element (`nums[i]`) is equal to the previous element (`nums[i-1]`) plus 1, it means the current element is part of a consecutive sequence. In this case, the `current` counter is incremented.
            
        * If the current element is not equal to the previous element, it means the current element is not part of the current consecutive sequence. The `current` counter is reset to 1.
            
    * The code also ensures that if consecutive elements are duplicates (have the same value), they do not affect the sequence length.
        
6. **Updating** `longest`:
    
    * After evaluating the conditions for each element, the `longest` length is updated if the `current` length is greater.
        
7. **Returning the Result:**
    
    * After processing all elements, the function returns the value of `longest`, which represents the length of the longest consecutive subsequence in the input array.
        

In summary, this code calculates the length of the longest consecutive subsequence by sorting the array and then iterating through it. It keeps track of the current consecutive sequence length and updates the maximum length encountered. The approach has a time complexity of O(n \* log n) due to the sorting step, where n is the length of the input array. The subsequent loop has a time complexity of O(n). This code uses a more concise approach compared to the previous one, achieving the same result.