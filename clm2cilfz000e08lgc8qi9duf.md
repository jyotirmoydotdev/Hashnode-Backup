---
title: "Minimum Window Substring - Leetcode 79"
datePublished: Sat Sep 02 2023 18:16:52 GMT+0000 (Coordinated Universal Time)
cuid: clm2cilfz000e08lgc8qi9duf
slug: leetcode-0079
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693678457322/e0e88692-e5e0-4c7e-8cdd-7f05b6455ed5.jpeg
tags: go, leetcode

---

# Problem - Leetcode

Given two strings `s` and `t` of lengths `m` and `n` respectively, return *the* ***minimum window***

***substring***

*of* `s` *such that every character in*`t`*(****including duplicates****) is included in the window*. If there is no such substring, return the *empty string*`""`.

The test cases will be generated such that the answer is **unique**.

 **Example 1:**

```plaintext
Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
```

**Example 2:**

```plaintext
Input: s = "a", t = "a"
Output: "a"
Explanation: The entire string s is the minimum window.
```

**Example 3:**

```plaintext
Input: s = "a", t = "aa"
Output: ""
Explanation: Both 'a's from t must be included in the window.
Since the largest window of s only has one 'a', return empty string.
```

**Constraints:**

* `m == s.length`
    
* `n == t.length`
    
* `1 <= m, n <= 10<sup>5</sup>`
    
* `s` and `t` consists of uppercase and lowercase English letters.
    

 **Follow-up:** Could you find an algorithm that runs in `O(m + n)` time?

# Solution in Golang

```go
func minWindow(s string, t string) string {
	start, end := 0, 0
	targetCharacterFrequency := make(map[uint8]int)
	currentCharacterFrequency := make(map[uint8]int)
	distinctCharacterCount := 0
	minSubstring := ""

	for index := range t {
		targetCharacterFrequency[t[index]]++
	}

	for end < len(s) {
		currentCharacterFrequency[s[end]]++
		if targetCharacterFrequency[s[end]] != 0 &&
			targetCharacterFrequency[s[end]] == currentCharacterFrequency[s[end]] {
			distinctCharacterCount++
		}

		for distinctCharacterCount == len(targetCharacterFrequency) {
			if minSubstring == "" {
				minSubstring = s[start:end+1]
			}
			if end - start + 1 < len(minSubstring) {
				minSubstring = s[start:end+1]
			}

			currentCharacterFrequency[s[start]]--
			if currentCharacterFrequency[s[start]] < targetCharacterFrequency[s[start]] {
				distinctCharacterCount--
			}

			start++
		}
		end++
	}

	return minSubstring
}
```

This code is an implementation of the sliding window technique to find the minimum window in string 's' which contains all characters from string 't'. The idea is to maintain two pointers, 'start' and 'end', and slide the window to find the smallest substring in 's' that contains all the characters from 't'.

Here's a detailed breakdown of the code:

1. Initialize variables:
    
    * `start` and `end` are pointers to maintain the current window.
        
    * `targetCharacterFrequency` is a map to store the frequency of characters in string 't'.
        
    * `currentCharacterFrequency` is a map to store the frequency of characters in the current window.
        
    * `distinctCharacterCount` keeps track of the number of distinct characters in the current window.
        
    * `minSubstring` is initially an empty string and will be updated with the minimum substring containing all characters from 't'.
        
2. Loop through string 't' to populate `targetCharacterFrequency` with character frequencies.
    
3. Start a while loop with the 'end' pointer moving through the string 's':
    
    * Increment the frequency of the character at 'end' in `currentCharacterFrequency`.
        
    * Check if the character at 'end' is one of the target characters (from 't') and if its frequency in the current window matches the target frequency. If it does, increment `distinctCharacterCount`.
        
4. Inside the while loop, another nested while loop:
    
    * Check if `distinctCharacterCount` is equal to the total number of distinct characters in 't'. If it is, it means the current window contains all characters from 't'.
        
    * Update `minSubstring` if it's empty or if the current window is smaller than the previously found minimum.
        
    * Decrement the frequency of the character at 'start' in `currentCharacterFrequency`.
        
    * If the frequency of the character at 'start' becomes less than the target frequency, decrement `distinctCharacterCount`.
        
    * Move the 'start' pointer to the right to try to find a smaller window containing all characters.
        
5. Move the 'end' pointer to the right to expand the window and continue the process.
    
6. Once the while loop finishes, return `minSubstring`, which will be the minimum window containing all characters from 't'.
    

In summary, this code efficiently finds the minimum window in string 's' that contains all characters from string 't' by maintaining a sliding window and tracking character frequencies. It's a common algorithmic technique used for substring search problems.