---
title: "Valid Palindrome - Leetcode 125"
datePublished: Wed Aug 16 2023 15:55:01 GMT+0000 (Coordinated Universal Time)
cuid: clldwyp4k00020amfho03elva
slug: leetcode-0125
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692201059261/f5906192-8a14-4626-821a-9096eafbc223.jpeg
tags: golang, dsa, leetcode

---

# Problem - Leetcode

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` *if it is a* ***palindrome****, or* `false` *otherwise*.

**Example 1:**

```go
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

**Example 2:**

```go
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

**Example 3:**

```go
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

**Constraints:**

* `1 <= s.length <= 2 * 10<sup>5</sup>`
    
* `s` consists only of printable ASCII characters.
    

# Answer-1 in Golang

```go
func isPalindrome(s string) bool {
	i, j := 0, len(s)-1
	arr := []rune(s)

	for i < j {
		left := unicode.ToLower(arr[i])
		right := unicode.ToLower(arr[j])

		if !isLetterOrDigit(left) {
			i++
			continue
		}

		if !isLetterOrDigit(right) {
			j--
			continue
		}

		if left != right {
			return false
		}

		i++
		j--
	}

	return true
}

func isLetterOrDigit(s rune) bool {
	return unicode.IsLetter(s) || unicode.IsDigit(s)
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692198456762/cef5395d-cc61-48c2-b60d-78cc29083fab.png align="center")

This code defines a function `isPalindrome` that takes a string `s` as input and returns a boolean indicating whether the given string is a palindrome or not. A palindrome is a string that reads the same forwards and backwards.

1. `i` and `j` are initialized to 0 and `len(s) - 1`, respectively. These two pointers are used to iterate through the string from both ends.
    
2. The input string `s` is converted to a rune slice called `arr`. Runes are Unicode characters that represent each character in the string.
    
3. The main loop runs while `i` is less than `j`. This loop compares characters from the start and end of the string towards the center.
    
4. Inside the loop:
    
    * The characters at `i` and `j` indices in the `arr` are converted to lowercase using `unicode.ToLower`. This step is taken to make the comparison case-insensitive.
        
    * The `isLetterOrDigit` function is used to check if the character at the `i`\-th position is a letter or digit. If it's not, `i` is incremented, and the loop continues to the next iteration. This step skips non-alphanumeric characters from the comparison.
        
    * Similarly, the `isLetterOrDigit` function is used to check if the character at the `j`\-th position is a letter or digit. If it's not, `j` is decremented, and the loop continues to the next iteration. This step also skips non-alphanumeric characters from the comparison.
        
    * If both the left (`i`\-th position) and right (`j`\-th position) characters are valid letters or digits, their lowercase versions are compared. If they are not equal, the function returns `false`, indicating that the string is not a palindrome.
        
    * If the characters match, both `i` and `j` are incremented and decremented, respectively, to continue comparing the next characters.
        
5. After the loop finishes, if all the character comparisons have matched, the function returns `true`, indicating that the string is a palindrome.
    
6. The `isLetterOrDigit` function takes a rune as input and returns `true` if the rune is a letter or digit, based on the `unicode.IsLetter` and `unicode.IsDigit` functions.
    

In summary, the code efficiently checks if a given string is a palindrome by iterating through the string from both ends, skipping non-alphanumeric characters, and performing case-insensitive comparisons. It does this in linear time, making it an efficient approach for checking palindromes.

# Answer-2 Top Runtime and Memory in Golang

```go
func isPalindrome(s string) bool {
	start, end := 0, len(s)-1

	for start < end {
		for start < end && !unicode.IsLetter(rune(s[start])) && (s[start] < '0' || s[start] > '9') {
			start++
		}
		for start < end && !unicode.IsLetter(rune(s[end])) && (s[end] < '0' || s[end] > '9') {
			end--
		}
		if start < end && unicode.ToUpper(rune(s[start])) != unicode.ToUpper(rune(s[end])) {
			return false
		}
		start++
		end--
	}

	return true
}
```

This code defines a function `isPalindrome` in the Go programming language that checks whether a given string is a palindrome while considering only alphanumeric characters. Let's break down the code step by step:

1. The function `isPalindrome` takes a single argument `s`, which is a string that needs to be checked for palindrome property.
    
2. Two variables, `start` and `end`, are initialized to 0 and the length of the input string minus 1, respectively. These variables will be used to traverse the string from both ends towards the middle.
    
3. The code enters a loop with the condition `start < end`. This loop will continue until the `start` pointer crosses the `end` pointer.
    
4. Inside the loop, there are two nested loops. These loops are used to skip non-alphanumeric characters from both ends of the string. The condition for both loops is that the `start` pointer must be less than the `end` pointer, and the character at the current position should not be a letter (using `unicode.IsLetter`) and should not be a digit (checked with `(s[start] < '0' || s[start] > '9')`).
    
5. If a non-alphanumeric character is found at the `start` position, the `start` pointer is incremented to skip it. Similarly, if a non-alphanumeric character is found at the `end` position, the `end` pointer is decremented to skip it. These loops ensure that the code only compares alphanumeric characters while ignoring other characters.
    
6. After skipping non-alphanumeric characters, the code checks whether the alphanumeric characters at the `start` and `end` positions are equal, ignoring case. This is done using `unicode.ToUpper` to convert both characters to uppercase and then comparing them. If they are not equal, the function immediately returns `false`, indicating that the string is not a palindrome.
    
7. If the characters at the `start` and `end` positions are equal, the `start` pointer is incremented, and the `end` pointer is decremented, effectively moving towards the middle of the string.
    
8. The process continues until the `start` pointer crosses the `end` pointer. If the loop completes without any inequality between corresponding characters, the function returns `true`, indicating that the input string is a palindrome.
    

In summary, this code defines a function that determines whether a given string is a palindrome by considering only alphanumeric characters while ignoring non-alphanumeric characters and case differences. It does this by using two pointers that traverse the string from both ends towards the middle, comparing corresponding characters along the way.