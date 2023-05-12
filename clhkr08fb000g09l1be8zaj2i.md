---
title: "Contains Duplicate - LC217"
datePublished: Fri May 12 2023 16:03:49 GMT+0000 (Coordinated Universal Time)
cuid: clhkr08fb000g09l1be8zaj2i
slug: contains-duplicate-lc217
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683907283512/dbca7cf6-1a2b-49de-a8c3-21bdc2be5f90.jpeg
tags: cpp, sorting, array, hash-table, leetcode

---

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

```plaintext
Input: nums = [1,2,3,1]
Output: true
```

```plaintext
Input: nums = [1,2,3,4]
Output: false
```

```plaintext
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

**Constraints:**

* `1 <= nums.length <= 10<sup>5</sup>`
    
* `-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>`
    

---

## Answer

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> nums1;
        for(auto n : nums){
        nums1.insert(n);
        }
        if (nums.size()!=nums1.size()){
            return true;
        }
        return false;
    }
};
```

This code implements a function called `containsDuplicate` that takes a vector of integers `nums` as input and returns a boolean value indicating whether the vector contains any duplicate elements.

Here's a step-by-step explanation of how the code works:

1. Create an empty unordered set called `nums1`. An unordered set is a data structure that stores unique elements in no particular order. It is used here to check for duplicate elements efficiently.
    
2. Iterate over each integer `n` in the input vector `nums`.
    
    * Insert the integer `n` into the unordered set `nums1` using the `insert` function. Since the set only allows unique elements, if `n` is already present in the set, it will not be inserted again.
        
3. After the iteration, the unordered set `nums1` will contain unique elements from the input vector `nums`. If there are any duplicate elements in `nums`, they would not have been inserted into the set.
    
4. Check if the size of the input vector `nums` is different from the size of the unordered set `nums1`. If they are different, it means that there were duplicate elements in the input vector.
    
    * If the sizes are different, return `true` to indicate that the vector contains duplicates.
        
5. If the sizes are the same, it means that all elements in the vector are unique and there are no duplicates.
    
    * In this case, return `false` to indicate that the vector does not contain duplicates.
        

In summary, the code uses an unordered set to efficiently check for duplicate elements by inserting each element from the vector into the set. It then compares the sizes of the vector and the set to determine if there are any duplicates.