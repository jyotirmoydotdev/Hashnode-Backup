---
title: "Valid Anagram - Leetcode 242"
datePublished: Tue Aug 08 2023 19:16:33 GMT+0000 (Coordinated Universal Time)
cuid: clhleikz7000809kw1hru1jvf
slug: valid-anagram-leetcode-242
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691522078514/40ab3e22-2f4c-4e93-99ce-8a74d1eff8d0.jpeg
tags: cpp, sorting, string, hash-table, leetcode

---

# Problem

Given two strings `s` and `t`, return `true` *if* `t` *is an anagram of* `s`*, and* `false` *otherwise*.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

```plaintext
Input: s = "anagram", t = "nagaram"
Output: true
```

```plaintext
Input: s = "rat", t = "car"
Output: false
```

**Constraints:**

* `1 <= s.length, t.length <= 5 * 10<sup>4</sup>`
    
* `s` and `t` consist of lowercase English letters.
    

# Answer in Golang

```go
func isAnagram(s string, t string) bool {
	if len(s) != len(t) {
		return false
	}

	mapS, mapT := make(map[uint8]int), make(map[uint8]int)

	for i := 0; i < len(s); i++ {
		mapS[s[i]]++
		mapT[t[i]]++
	}
	for key, Value := range mapS {
		if mapT[key] != Value {
			return false
		}
	}

	return true
}
```

This code defines a function called `isAnagram` that takes two string inputs, `s` and `t`, and returns a boolean value indicating whether they are anagrams of each other.

An anagram is a word or phrase formed by rearranging the letters of another word or phrase, typically using all the original letters exactly once. In this case, the code is checking if two strings, `s` and `t`, are anagrams of each other.

Let’s break down the code step by step:

1. The function `isAnagram` takes two string parameters, `s` and `t`, and returns a boolean value indicating whether they are anagrams of each other.
    
2. The first check compares the lengths of strings `s` and `t`. If they are not of the same length, it means they cannot be anagrams. In this case, the function immediately returns `false`.
    
3. Two maps, `mapS` and `mapT`, are initialized using the built-in `make` function. These maps will be used to store the frequency of characters in strings `s` and `t` respectively. The keys of these maps are of type `uint8`, representing byte values (essentially ASCII values), and the values are integers representing the frequency of each character.
    
4. A loop runs through each character of strings `s` and `t` simultaneously (since they have the same length). Inside the loop, the frequencies of characters in both `mapS` and `mapT` are updated. This is achieved by using the characters as keys and incrementing their corresponding values in the maps.
    
5. After populating both maps with character frequencies, a second loop iterates through the keys in `mapS`. For each key, it checks if the frequency of that character in `mapT` is equal to the frequency in `mapS`. If not, it means that the character frequencies between the two strings are not the same, which would indicate that the strings are not anagrams. In this case, the function returns `false`.
    
6. If the second loop completes without returning `false`, it means that the character frequencies in both maps are the same, which implies that the input strings `s` and `t` are anagrams of each other. Thus, the function returns `true`.
    

In summary, this code determines whether two input strings are anagrams by comparing their lengths and checking the frequencies of characters in each string. If the lengths are different or if the character frequencies do not match, the function returns `false`, indicating that the strings are not anagrams. If the character frequencies are the same, the function returns `true`, indicating that the strings are anagrams.