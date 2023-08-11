---
title: "Group Anagrams - Leetcode 49"
datePublished: Fri Aug 11 2023 14:01:35 GMT+0000 (Coordinated Universal Time)
cuid: clhowbl0k000d09mnce9n8xkj
slug: group-anagrams-leetcode-49
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691762469331/e6ed6271-744c-4224-a7bc-79e5a131404d.jpeg
tags: sorting, string, array, hash-table

---

Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

```plaintext
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

```plaintext
Input: strs = [""]
Output: [[""]]
```

```plaintext
Input: strs = ["a"]
Output: [["a"]]
```

**Constraints:**

* `1 <= strs.length <= 10<sup>4</sup>`
    
* `0 <= strs[i].length <= 100`
    
* `strs[i]` consists of lowercase English letters.
    

# Answer in Golang

```go
func groupAnagrams(strs []string) [][]string {
	anagramMap := make(map[[26]int][]string)
	for _, s := range strs {
		var count [26]int
		for _, c := range s {
			count[c-'a']++
		}
		anagramMap[count] = append(anagramMap[count], s)
	}
	result := make([][]string, len(anagramMap))
	idx := 0
	for _, v := range anagramMap {
		result[idx] = v
		idx++
	}
	return result
}
```

The provided Go code step-by-step:

1. The function `groupAnagrams` takes a slice of strings called `strs` as input and returns a 2D slice of strings where each inner slice represents a group of anagrams.
    
2. Inside the function, an empty map named `anagramMap` is created. This map is used to store anagrams grouped by their character frequency patterns. The keys in this map are arrays of integers with length 26 (representing the count of each lowercase letter in the English alphabet) and the values are slices of strings containing anagrams with the same character frequency pattern.
    
3. A loop iterates through each string `s` in the `strs` slice.
    
4. Inside the loop, an array of integers named `count` with a length of 26 is created. This array will store the frequency of each lowercase letter in the current string `s`.
    
5. Another loop iterates through each character `c` in the string `s`.
    
6. For each character `c`, the frequency count for the corresponding lowercase letter is incremented in the `count` array. This is done by subtracting the ASCII value of 'a' from the character `c`, resulting in an index that corresponds to the position of the letter in the `count` array.
    
7. After processing all the characters in the string `s`, the `count` array now holds the frequency of each letter in that string.
    
8. The string `s` is appended to the slice of strings associated with the calculated `count` array in the `anagramMap`. This effectively groups strings with the same character frequency pattern together.
    
9. The above steps are repeated for all strings in the input `strs`, populating the `anagramMap` map.
    
10. After processing all input strings, a new 2D slice of strings named `result` is created, with a length equal to the number of unique character frequency patterns (i.e., the number of keys in `anagramMap`).
    
11. A variable `idx` is initialized to 0. This variable will be used to fill in the `result` slice.
    
12. A loop iterates through the values (which are slices of strings) in the `anagramMap`.
    
13. For each value (slice of strings), the value is assigned to the `result` slice at the index `idx`.
    
14. The `idx` variable is incremented to prepare for the next iteration.
    
15. Once all values from the `anagramMap` have been assigned to the `result` slice, the `result` slice is populated with groups of anagrams.
    
16. Finally, the function returns the populated `result` slice, where each inner slice represents a group of anagrams with the same character frequency pattern.
    

In summary, this code takes a list of strings, groups them based on their anagram patterns using a map, and returns a 2D slice containing these groups of anagrams.