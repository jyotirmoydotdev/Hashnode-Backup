---
title: "Two Sum - LC1"
datePublished: Sun May 14 2023 14:37:38 GMT+0000 (Coordinated Universal Time)
cuid: cld3pgnm3000209mldhk29u5q
slug: leetcode-1-two-sum
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684075201268/6b16ce71-d3b2-4d75-b250-3e5bf38a0487.jpeg
tags: cpp, array, hash-table, leetcode

---

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to* `target`.

You may assume that each input would have ***exactly* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

```plaintext
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

```plaintext
Input: nums = [3,2,4], target = 6
Output: [1,2]pl
```

```plaintext
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

The code is written in C++ and aims to find a pair of indices in a given vector (`nums`) that sum up to a specific target value. Here's an explanation of the code:

1. The function `twoSum` takes two parameters: `nums`, a reference to a vector of integers, and `target`, an integer representing the target sum.
    
2. It declares a vector of integers called `ans` to store the resulting indices that sum up to the target.
    
3. The outer `for` loop iterates over each element of the `nums` vector. It uses the variable `i` as the index of the first number in a potential pair.
    
4. The inner `for` loop starts from `i + 1` and iterates over the remaining elements of the `nums` vector. It uses the variable `j` as the index of the second number in the pair.
    
5. Inside the inner loop, the condition `(nums[i] + nums[j]) == target` checks if the sum of the current pair of numbers equals the target value.
    
6. If the condition is true, the indices `i` and `j` are added to the `ans` vector using the `push_back` function.
    
7. After both loops have finished iterating, the function returns the `ans` vector containing the indices of the pair that sum up to the target.
    

In summary, the code uses a nested loop to compare each pair of numbers in the vector `nums`. If a pair with a sum equal to the target is found, the indices of that pair are stored in the `ans` vector, which is then returned as the result.