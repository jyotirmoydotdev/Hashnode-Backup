---
title: "Group Anagrams - LC49"
datePublished: Mon May 15 2023 13:43:42 GMT+0000 (Coordinated Universal Time)
cuid: clhowbl0k000d09mnce9n8xkj
slug: group-anagrams-lc49
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684158079342/1026f47f-3050-4d27-a7a9-adfc678eb22a.jpeg
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
    

---

# Answer

```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
      vector<vector<string>> ans;
      map<string, vector<string>> mp;
      for (string s : strs) {
        string sorted_s = s;
        sort(sorted_s.begin(), sorted_s.end());
        mp[sorted_s].push_back(s);
      }
      for (auto it : mp) {
        ans.push_back(it.second);
      }
      return ans;
    }
};
```

The code is an implementation of a function called `groupAnagrams`, which takes a vector of strings (`strs`) as input and groups the anagrams together.

Here's a step-by-step explanation of the code:

1. Declare and initialize the `ans` variable as a vector of vectors of strings. This will store the final groups of anagrams.
    
2. Declare and initialize the `mp` variable as a map of strings to vectors of strings. This will be used to group the anagrams based on their sorted versions.
    
3. Start a loop to iterate over each string `s` in the input vector `strs`.
    
4. Inside the loop, create a variable `sorted_s` and assign it the value of `s`. This variable will be used to store the sorted version of the current string.
    
5. Sort the characters of `sorted_s` using the `sort` function from the `<algorithm>` header. This will rearrange the characters in ascending order.
    
6. Use `mp[sorted_s]` to access the vector associated with the sorted string `sorted_s` in the map `mp`. This will return a reference to the vector.
    
7. Push the current string `s` into the vector associated with `sorted_s` in `mp`. This effectively groups all the anagrams `s` together based on their sorted versions.
    
8. After the loop, iterate over each key-value pair (`it`) In the map `mp`.
    
9. Access the value (vector of strings) of the current key-value pair (`it.second`) and push it into the `ans` vector.
    
10. Finally, return the `ans` vector, which contains the grouped anagrams.
    

In summary, the code iterates over each string in the input vector, sorts each string to find its sorted version, and then groups the anagrams together based on their sorted versions using a map. The resulting groups are stored in a vector and returned as the output.