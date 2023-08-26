---
title: "Longest Substring Without Repeating Characters - Leetcode 3"
datePublished: Sat Aug 26 2023 14:53:14 GMT+0000 (Coordinated Universal Time)
cuid: clls55rcd000309ladis29sif
slug: leetcode-003
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693061209415/a39e0123-7cd6-4452-ab92-b00d5fc872a6.jpeg
tags: go, leetcode

---

# Problem - Leetcode

Given a string `s`, find the length of the **longest substring** without repeating characters.

**Example 1:**

```sql
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**

```sql
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```sql
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Constraints:**

* `0 <= s.length <= 5 * 10<sup>4</sup>`
    
* `s` consists of English letters, digits, symbols and spaces.
    

# Answer-1 in Golang

```go
func lengthOfLongestSubstring(s string) int {
    charSet := make(map[byte]bool)
    l := 0
    res := 0 
    for r, _ := range s {
        for charSet[s[r]] {
            delete(charSet,s[l])
            l++
        }
        charSet[s[r]] = true
        res = max(res, r-l+1)
    }
    return res
}
func max(a,b int) int {
    if a > b{
        return a
    }
    return b
}
```

This code defines a function `lengthOfLongestSubstring` that takes a string `s` as input and calculates the length of the longest substring within that string, where all characters in the substring are unique. Let's break down the code step by step:

1. `charSet := make(map[byte]bool)`: This line initializes an empty map called `charSet`, which will be used to keep track of characters encountered in the current substring.
    
2. `l := 0`: This initializes a variable `l` (short for "left") to 0. It represents the left pointer of the current substring.
    
3. `res := 0`: This initializes a variable `res` (short for "result") to 0. It will store the length of the longest substring found.
    
4. The first `for` loop iterates over the characters in the input string `s`. It uses two variables, `r` and `_`, where `r` represents the current position (right pointer) in the string.
    
5. Inside the first loop, there's another loop: `for charSet[s[r]]`. This loop checks whether the current character `s[r]` is already present in the `charSet` map. If it is, that means the current character is a repeating character, so the algorithm needs to shrink the substring by moving the left pointer (`l`) to the right until the repeated character is removed from the substring.
    
6. Inside the inner loop, `delete(charSet, s[l])` removes the character at the `l` position from the `charSet` map, effectively shifting the left pointer to the right.
    
7. After the inner loop, `charSet[s[r]] = true` adds the current character to the `charSet` map, indicating its presence in the current substring.
    
8. `res = max(res, r-l+1)`: This calculates the length of the current substring (from `l` to `r`) and compares it to the current maximum length stored in `res`. Whichever is greater becomes the new value of `res`.
    
9. The function `max(a, b int)` is defined to return the maximum of two integers `a` and `b`.
    
10. Finally, the function returns the value of `res`, which represents the length of the longest substring with unique characters.
    

In summary, this code uses a sliding window approach to find the longest substring without repeating characters within the given input string `s`. The `charSet` map keeps track of characters in the current substring, and the left and right pointers (`l` and `r`) control the window boundaries. The result is stored in the `res` variable and returned at the end.