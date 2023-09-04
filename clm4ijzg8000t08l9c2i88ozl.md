---
title: "Valid Parentheses - Leetcode 20"
datePublished: Mon Sep 04 2023 06:41:27 GMT+0000 (Coordinated Universal Time)
cuid: clm4ijzg8000t08l9c2i88ozl
slug: leetcode-0020
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693809335915/c6084627-d982-470c-92b0-c4bf923aa21e.jpeg
tags: go, leetcode

---

# Problem - Leetcode

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
    
2. Open brackets must be closed in the correct order.
    
3. Every close bracket has a corresponding open bracket of the same type.
    

**Example 1:**

```go
Input: s = "()"
Output: true
```

**Example 2:**

```go
Input: s = "()[]{}"
Output: true
```

**Example 3:**

```go
Input: s = "(]"
Output: false
```

**Constraints:**

* `1 <= s.length <= 10<sup>4</sup>`
    
* `s` consists of parentheses only `'()[]{}'`.
    

# Solution in Golang

```go
func isValid(s string) bool {
    stack := make([]byte,0)
    pairs := map[byte]byte{
		'}' : '{',
		']' : '[',
		')' : '(',
    }
    for _, char := range []byte(s){
        pair, ok := pairs[char]
        if !ok {
            stack = append(stack, char)
            continue
        }
        if len(stack) == 0 {
            return false
        }
        if stack[len(stack)-1] != pair{
            return false
        }
        stack = stack [:len(stack)-1]
    }
    return len(stack) == 0
}
```

This code defines a function `isValid(s string) bool` that checks if a given input string `s` contains valid pairs of parentheses, square brackets, and curly braces. It utilizes a stack data structure to perform this validation. Here's a detailed explanation of the code:

1. `stack := make([]byte, 0)`: This line initializes an empty byte slice called `stack`, which will be used as a stack to keep track of the opening parentheses, square brackets, and curly braces encountered in the input string.
    
2. `pairs := map[byte]byte{...}`: This line creates a map called `pairs` that defines the valid pairs of closing and opening characters. For example, '}' is paired with '{', '\]' is paired with '\[', and ')' is paired with '('. This map is used to check if the closing character corresponds to the most recent opening character in the stack.
    
3. The code then iterates through each character `char` in the input string `s` using a `for` loop.
    
4. `pair, ok := pairs[char]`: This line attempts to look up the corresponding opening character for the current `char` in the `pairs` map. If `char` is not one of the closing characters ('}', '\]', or ')'), `ok` will be `false`, and `pair` will be the zero value for `byte`.
    
5. `if !ok { ... }`: If `char` is not a closing character, it means it's an opening character ('{', '\[', or '('), so it's appended to the `stack`. This step is necessary to keep track of the opening characters until their corresponding closing character is encountered.
    
6. `if len(stack) == 0 { return false }`: If `char` is a closing character and the `stack` is empty, it means there's no corresponding opening character in the stack. In this case, the function returns `false` immediately because the string is not valid.
    
7. `if stack[len(stack)-1] != pair { return false }`: If `char` is a closing character and the `stack` is not empty, this line compares the most recent opening character in the stack (i.e., `stack[len(stack)-1]`) with the expected opening character (`pair`) based on the `pairs` map. If they don't match, the function returns `false` because the string is not valid.
    
8. `stack = stack[:len(stack)-1]`: If the closing character matches the expected opening character, the opening character is removed from the stack, indicating that the pair has been successfully closed.
    
9. After processing all characters in the input string, the function checks if the `stack` is empty. If it is, it means all opening characters have been successfully closed, and the function returns `true`. Otherwise, if there are unmatched opening characters left in the stack, it returns `false`.
    

In summary, this code uses a stack to keep track of opening characters and checks if each closing character matches the most recent opening character encountered. If at the end of processing the input string the stack is empty, it returns `true`, indicating that the input string contains valid pairs of parentheses, square brackets, and curly braces; otherwise, it returns `false`.