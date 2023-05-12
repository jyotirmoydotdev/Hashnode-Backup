---
title: "Two Sum - LC1"
datePublished: Thu Jan 19 2023 23:09:42 GMT+0000 (Coordinated Universal Time)
cuid: cld3pgnm3000209mldhk29u5q
slug: leetcode-1-two-sum
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1674169293465/c35667b8-ed4b-4845-b94f-bf1235ea7a9b.jpeg
tags: cpp, leetcode

---

# Question

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to* `target`.

You may assume that each input would have ***exactly* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

**Example 1:**

```xml
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```xml
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```xml
Input: nums = [3,3], target = 6
Output: [0,1]
```

**Constraints:**

* `2 <= nums.length <= 10<sup>4</sup>`
    
* `-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>`
    
* `-10<sup>9</sup> <= target <= 10<sup>9</sup>`
    
* **Only one valid answer exists.**
    

# Answer

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
      vector<int> ans;
      for (int i=0;i<nums.size();i++){
        for (int j=i+1;j<nums.size();j++){
            if ((nums[i]+nums[j])==target){
                ans.push_back(i);
                ans.push_back(j);
            }
        }
    } 
    return ans; 
    }
};
```

The solution we will be using is brute force, the function takes two variables one is nums which contain the vector and the other one is a target which we need to find by summing two indexes in the vector and if we got the sum we will return the index in a new vector.

Before we start the for loops first we need to make an empty vector, which we will call `ans`. we will use a nested for loop to check if the target is present in the array. The first loop starts with the i'th which is 0 and stops at (vector size - 1) and the inner for loop starts at i+1 and stops as same as (vector size -1), if the index i and i+n (where n is a number less than vector size but greater than i) is equal to the target value we will push the index to the new array `ans` and return it. It has O(n^2) time complexity as it has two nested loops. Below you can see an animation of how this program works.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674166201237/530d630d-4026-40e8-b755-76cfadc4027d.gif align="center")

%%[links]