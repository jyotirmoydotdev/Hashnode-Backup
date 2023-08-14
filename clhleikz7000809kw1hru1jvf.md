---
title: "Valid Anagram - Leetcode 242"
datePublished: Tue Aug 08 2023 19:16:33 GMT+0000 (Coordinated Universal Time)
cuid: clhleikz7000809kw1hru1jvf
slug: leetcode-0242
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691522078514/40ab3e22-2f4c-4e93-99ce-8a74d1eff8d0.jpeg
tags: cpp, sorting, string, hash-table, leetcode

---

# Problem - Leetcode

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
    

# Answer-1 in Golang

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

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692027616140/7570f755-e704-44ca-84ed-f7fa18eb0fb9.png align="center")

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

# Answer-2 Top Runtime in Golang

```go
func isAnagram(s string, t string) bool {
    m := make(map[rune]int, len(s))
    for _, r := range s {
        m[r]++
    }
    for _, r := range t {
        m[r]--
    }
    for _, v := range m {
        if v != 0 {
            return false
        }
    }
    return true
}
```

This code defines a function called `isAnagram` that checks whether two input strings `s` and `t` are anagrams of each other. Anagrams are words or phrases that have the same characters but in a different order.

Here's a detailed explanation of how the code works:

1. The function `isAnagram` takes two string arguments, `s` and `t`.
    
2. It starts by creating an empty map named `m` using the `make` function. This map will store the frequency of each character in the `s` string. The map's keys are of type `rune` (Unicode characters), and the values are integers representing the frequency of each character.
    
3. The first loop iterates over each character `r` in the `s` string. It increments the value associated with the character `r` in the map `m` by 1. This step counts the frequency of characters in the `s` string.
    
4. The second loop iterates over each character `r` in the `t` string. It decrements the value associated with the character `r` in the map `m` by 1. This step simulates subtracting the frequency of characters present in the `t` string.
    
5. After both loops complete, the map `m` will hold the difference in character frequencies between the two strings. If `s` and `t` are anagrams, the map `m` should have all values equal to 0, because the frequencies should cancel each other out.
    
6. The final loop iterates over the values in the map `m`. If any value is not equal to 0, it means the frequencies of characters in `s` and `t` did not cancel out, indicating that the strings are not anagrams. In this case, the function returns `false`.
    
7. If all values in the map `m` are equal to 0, then the strings `s` and `t` are anagrams, and the function returns `true`.
    

In summary, the code uses a map to store the frequency of characters in the input strings and then checks if the frequency differences between the strings are all zero to determine if the strings are anagrams.

# Answer-3 Top Memory in Golang

```go
func isAnagram(s string, t string) bool {
    if len(s) != len(t) {
        return false
    }
    m := make(map[byte]int, 0)
    for i := 0; i < len(s); i++ {
        m[s[i]]++
        m[t[i]]--
    }
    for _, v := range m {
        if v != 0 {
            return false
        }
    }
    return true
}
```

This code defines a function called `isAnagram` that takes two string parameters `s` and `t` and returns a boolean value indicating whether the two input strings are anagrams of each other or not. Anagrams are words or phrases that are formed by rearranging the letters of another word or phrase.

Here's a breakdown of how the code works:

1. The function begins by checking if the lengths of strings `s` and `t` are equal. If they are not equal, it immediately returns `false`, since two strings with different lengths cannot be anagrams of each other.
    
2. If the lengths of the strings are equal, the function proceeds to create a map called `m` to keep track of the frequency of each character in the strings. The map is of type `map[byte]int`, where the keys are individual characters (represented as bytes) and the values are integers representing the frequency of each character.
    
3. A loop runs through each character index from 0 to the length of the strings minus 1 (i.e., for each character in the strings). Inside the loop:
    
    * The frequency count of the character `s[i]` is increased in the map `m` using the `++` operator.
        
    * The frequency count of the character `t[i]` is decreased in the map `m` using the `--` operator.
        
4. After both strings have been processed in the loop, the code enters another loop using a range-based iteration on the values of the map `m`. For each value `v` in the map:
    
    * If `v` is not equal to 0, it means that the frequencies of characters in the two strings `s` and `t` are not balanced, indicating that they are not anagrams. In this case, the function returns `false`.
        
5. If all the values in the map `m` are equal to 0, it means that the frequencies of characters in the two strings are balanced, and the function returns `true`, indicating that the input strings `s` and `t` are indeed anagrams of each other.
    

To summarize, this code uses a character frequency map to determine whether two strings are anagrams by comparing the frequency of characters in each string. If the frequencies are the same for all characters, the strings are anagrams, and the function returns `true`. Otherwise, it returns `false`.