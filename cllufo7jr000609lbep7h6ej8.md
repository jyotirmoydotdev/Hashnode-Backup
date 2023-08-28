---
title: "Longest Repeating Character Replacement - Leetcode 424"
datePublished: Mon Aug 28 2023 05:23:04 GMT+0000 (Coordinated Universal Time)
cuid: cllufo7jr000609lbep7h6ej8
slug: leetcode-0424
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693200117453/0c455308-ad0f-415c-9cba-9e4875c70a65.jpeg
tags: go, leetcode

---

# Problem - Leetcode

You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.

Return *the length of the longest substring containing the same letter you can get after performing the above operations*.

**Example 1:**

```go
Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
```

**Example 2:**

```go
Input: s = "AABABBA", k = 1
Output: 4
Explanation: Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exists other ways to achive this answer too.
```

**Constraints:**

* `1 <= s.length <= 10<sup>5</sup>`
    
* `s` consists of only uppercase English letters.
    
* `0 <= k <= s.length`
    

# Answer-1 in Golang

```go
func characterReplacement(s string, k int) int {
	count := make(map[byte]int)
	maxF := 0
	left := 0
	result := 0
	for right, _ := range s {
		count[s[right]] = 1 + count[s[right]]
		maxF = max(maxF, count[s[right]])

		if (right-left+1)-maxF > k {
			count[s[left]] -= 1
			left++
		}
		result = max(result, right-left+1)
	}
	return result
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

This code defines a function called `characterReplacement` which takes two parameters: a string `s` and an integer `k`. The goal of the function is to find the length of the longest substring in which you can replace at most `k` characters to make all characters in the substring the same. Let's break down the code step by step:

1. `count := make(map[byte]int)`: This line initializes a map called `count` that will store the frequency of each character in the current substring.
    
2. `maxF := 0`: `maxF` keeps track of the maximum frequency of any character in the current substring.
    
3. `left := 0`: `left` is the left pointer of the sliding window that will be used to traverse the string.
    
4. `result := 0`: `result` will store the length of the longest valid substring found.
    
5. The code enters a loop that goes through each character in the input string `s`.
    
    a. `count[s[right]] = 1 + count[s[right]]`: This line increments the count of the character at the current `right` index in the `count` map.
    
    b. `maxF = max(maxF, count[s[right]])`: Update `maxF` with the maximum frequency seen so far.
    
    c. The code checks if the number of characters that need to be replaced in the current substring `(right - left + 1) - maxF` exceeds the given limit `k`.
    
    d. If the limit is exceeded, it means the substring needs more replacements than allowed. So, we move the `left` pointer one step to the right and decrease the frequency count of the character at that position.
    
    e. `result = max(result, right - left + 1)`: Update `result` with the maximum length of valid substrings encountered so far.
    
6. After the loop, the function returns the calculated `result`, which represents the length of the longest substring with at most `k` replacements allowed to make all characters the same.
    
7. There is also a helper function `max(a, b int) int` that returns the maximum of two integers.
    

In summary, this code uses a sliding window approach to find the length of the longest substring where you can replace at most `k` characters to make all characters the same. The `count` map keeps track of character frequencies within the current window, and the `maxF` variable tracks the most frequent character. By adjusting the window using the `left` pointer, the code keeps track of the maximum valid substring length encountered.