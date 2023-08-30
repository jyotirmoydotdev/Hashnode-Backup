---
title: "Permutation in String - Leetcode 567"
datePublished: Wed Aug 30 2023 14:32:04 GMT+0000 (Coordinated Universal Time)
cuid: cllxu5y7y000b0amldoxodwbb
slug: leetcode-0567
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693405774216/fca3f205-267f-4331-b9fe-cbaa00f3e3f3.jpeg
tags: go, leetcode

---

# Problem - Leetcode

Given two strings `s1` and `s2`, return `true` *if* `s2` *contains a permutation of* `s1`*, or* `false` *otherwise*.

In other words, return `true` if one of `s1`'s permutations is the substring of `s2`.

**Example 1:**

```go
Input: s1 = "ab", s2 = "eidbaooo"
Output: true
Explanation: s2 contains one permutation of s1 ("ba").
```

**Example 2:**

```go
Input: s1 = "ab", s2 = "eidboaoo"
Output: false
```

**Constraints:**

* `1 <= s1.length, s2.length <= 10<sup>4</sup>`
    
* `s1` and `s2` consists of lowercase English letters.
    

# Solution in Golang

```go
func checkInclusion(s1 string, s2 string) bool {
	if len(s1) > len(s2) {
		return false
	}
	s1Count, s2Count := [26]int{}, [26]int{}
	for i, _ := range s1 {
		s1Count[s1[i]-'a']++
		s2Count[s2[i]-'a']++
	}
	matches := 0
	for i := 0; i < 26; i++ {
		if s1Count[i] == s2Count[i] {
			matches += 1
		} else {
			matches += 0
		}
	}
	l := 0
	for r := len(s1); r < len(s2); r++ {
		if matches == 26 {
			return true
		}
		index := s2[r] - 'a'
		s2Count[index]++
		if s1Count[index] == s2Count[index] {
			matches++
		} else if s1Count[index]+1 == s2Count[index] {
			matches--
		}
		index = s2[l] - 'a'
		s2Count[index]--
		if s1Count[index] == s2Count[index] {
			matches++
		} else if s1Count[index]-1 == s2Count[index] {
			matches--
		}
		l++
	}
	return matches == 26
}
```

This code defines a Go function called `checkInclusion` that checks if one string, `s1`, is a permutation of any substring in another string, `s2`. In other words, it determines if all the characters in `s1` can be found in any order within `s2`. Here's a detailed explanation of how the code works:

1. The function starts by comparing the lengths of `s1` and `s2`. If `s1` is longer than `s2`, it immediately returns `false`, because it's not possible for `s1` to be a permutation of a longer string.
    
2. Two arrays, `s1Count` and `s2Count`, of size 26 (representing the lowercase English alphabet) are initialized to store the frequency of characters in `s1` and `s2`, respectively.
    
3. The code iterates through the characters in `s1` and increments the corresponding index in `s1Count` and `s2Count` arrays based on the ASCII value difference between the character and `'a'`.
    
4. The variable `matches` is initialized to track the number of characters that have matching frequencies between `s1` and the current substring of `s2`.
    
5. A loop from 0 to 25 iterates through each index representing a character in the arrays. If the character frequency in `s1` and `s2` match, `matches` is incremented.
    
6. The code then enters a sliding window approach to compare the substrings of `s2` with the length of `s1`. The `l` variable represents the left boundary of the sliding window, and the `r` variable represents the right boundary.
    
7. At each step, the code checks if `matches` is equal to 26 (representing all characters of the alphabet). If yes, it means `s1` is a permutation of the current substring of `s2`, and it immediately returns `true`.
    
8. The character at index `r` of `s2` is considered. Its frequency in `s2Count` is incremented. If this increment makes the frequency match that in `s1Count`, `matches` is incremented. If the frequency in `s2Count` exceeds `s1Count` by one, `matches` is decremented.
    
9. Similarly, the character at index `l` of the previous substring is considered. Its frequency in `s2Count` is decremented. If this decrement makes the frequency match that in `s1Count`, `matches` is incremented. If the frequency in `s2Count` becomes one less than `s1Count`, `matches` is decremented.
    
10. The `l` index is incremented to slide the window one step to the right.
    
11. The loop continues until the end of `s2` is reached. Finally, the function returns `true` if `matches` equals 26, indicating that all characters of `s1` are permuted within some substring of `s2`.
    

This code essentially uses the sliding window technique along with character frequency tracking to efficiently check for the permutation condition between two strings.