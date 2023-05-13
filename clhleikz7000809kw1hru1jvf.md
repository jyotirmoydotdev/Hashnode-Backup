---
title: "Valid Anagram"
datePublished: Sat May 13 2023 03:01:57 GMT+0000 (Coordinated Universal Time)
cuid: clhleikz7000809kw1hru1jvf
slug: valid-anagram
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683946821029/858eb713-41a9-4aee-bf82-84b38347e750.jpeg
tags: cpp, sorting, string, hash-table, leetcode

---

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
    

---

## Answer

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.size()!=t.size()){
        return false;
    }
    vector<char> s_vec(s.begin(), s.end());
    vector<char> t_vec(t.begin(), t.end());

    map<char,int> m;
    map<char,int> n;
    
    for (int i=0;i<s.size();i++){
        m[s_vec[i]]++;
    }
    for (int i=0;i<t.size();i++){
        n[t_vec[i]]++;
    }
    if (m==n){
        return true;
    }
    return false;
    }
};
```

The given code is an implementation of a function `isAnagram` that checks whether two input strings `s` and `t` are anagrams of each other.

Here's a step-by-step explanation of the code:

1. The function begins by comparing the lengths of strings `s` and `t` using the `size()` function. If the lengths are different, it means the strings cannot be anagrams, so the function returns `false`.
    
2. Next, two vectors `s_vec` and `t_vec` are created. These vectors are initialized with the characters from strings `s` and `t` respectively using the constructor that takes two iterators (begin and end) to specify the range. This allows us to iterate over the characters of the strings more easily.
    
3. Two maps, `m` and `n`, are created using the `map` container from the C++ Standard Library. These maps will store characters as keys and their respective counts as values. The map data structure provides an efficient way to store and access the frequency of each character.
    
4. A loop is used to iterate over the characters of string `s`. In each iteration, the corresponding character is used as a key in the map `m`, and its count is incremented by one. This step calculates the frequency of each character in string `s`.
    
5. Another loop is used to iterate over the characters of string `t`. In each iteration, the corresponding character is used as a key in the map `n`, and its count is incremented by one. This step calculates the frequency of each character in string `t`.
    
6. After counting the frequencies of characters in both strings, the code compares the two maps `m` and `n` using the `==` operator. If the maps are equal, it means that both strings contain the same characters with the same frequencies, indicating that they are anagrams. In this case, the function returns `true`.
    
7. If the maps are not equal, it means that the strings are not anagrams, so the function returns `false`.
    

In summary, the code checks whether two strings are anagrams by comparing the frequencies of their characters using maps. If the frequencies match, the strings are considered anagrams; otherwise, they are not.