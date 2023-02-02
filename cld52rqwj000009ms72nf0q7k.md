# 26. Remove Duplicates from Sorted Array

# Question

Read the Question here [https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

# Answer

```bash
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]

Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
```

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size() == 0) return 0;
        int i = 0;
        for (int j = 1; j < nums.size(); j++) {
            if (nums[i] != nums[j]) {
                i++;
                nums[i] = nums[j];
            }
        }
        return i + 1;
    }
};
```

This algorithm will work only on sorted array .

The function take a vector of integer (as a reference) and return an integer length of modifies vector after removing the duplicate integer. The function start with a if condition which check if the vector is empty and if it is true it will return 0 , if it is false and there is elements in vector it will continue. The algorithm uses two pointer `i` and `j` which itreate over the vector and and check for duplicate integers. The pointer `i` starts with the first element and the for loop where `j` starts with second element. Inside the for loop, if statement check if index `i` element is not equal to index `j` element, and if this is the case, this mean the index `j` element is not duplicate of index `i` element , so the element `j` is assigned to `i`+1. Then the pointer `i` is increment with 1. This process continue till the end of the vector.

At the end of the function, the pointer i+1 is returned as the length of the modified vector after removing duplicates.

Its time complextity is O(n) as we are using only 1 for loop so the time complexity in depend on the size of the vector.

This is how I debug, you can go through it to see what is happening in the code.

```bash
vector -> 0 0 1 1 1 2 2 3 3 4
i=0    -> ↑
j=1    ->   ↑
if (0!=0) ❌ 
----------------------------------------
Vector -> 0 0 1 1 1 2 2 3 3 4
i=0    -> ↑
j=2    ->     ↑
if (0!=1) ✅
    Vector -> 0 0 1 1 1 2 2 3 3 4
    i=1    ->   ↑
    nums[i] = nums[j]
    nums[1] = nums[2]
        0   =    1
    Vector modified (0 is replaced with 1)
                ↓
    Vector -> 0 1 1 1 1 2 2 3 3 4
----------------------------------------
Vector -> 0 1 1 1 1 2 2 3 3 4
i=1    ->   ↑
j=3    ->       ↑
if (1!=1)❌
----------------------------------------
Vector -> 0 1 1 1 1 2 2 3 3 4
i=1    ->   ↑
j=4    ->         ↑
if (1!=1) ❌
----------------------------------------
Vector -> 0 1 1 1 1 2 2 3 3 4
i=1    ->   ↑
j=5    ->           ↑
if (1!=2)✅
    Vector -> 0 1 1 1 1 2 2 3 3 4 
    i=2    ->     ↑
    nums[i] = nums[j]
    nums[2] = nums[5]
        1   =    2
    Vector modified (1 is replaced with 2)
                  ↓
    Vector -> 0 1 2 1 1 2 2 3 3 4
----------------------------------------
Vector -> 0 1 2 1 1 2 2 3 3 4
i=2    ->     ↑
j=6    ->             ↑
if (2!=2) ❌
----------------------------------------
Vector -> 0 1 2 1 1 2 2 3 3 4
i=2    ->     ↑
j=7    ->               ↑
if (2!=3)✅
    Vector -> 0 1 2 1 1 2 2 3 3 4 
    i=3    ->       ↑
    nums[i] = nums[j]
    nums[3] = nums[7]
        1   =    3
    Vector modified (1 is replaced with 3)
                    ↓
    Vector -> 0 1 2 3 1 2 2 3 3 4
----------------------------------------
Vector -> 0 1 2 3 1 2 2 3 3 4
i=3    ->       ↑
j=8    ->                 ↑
if (3!=3) ❌
----------------------------------------
Vector -> 0 1 2 3 1 2 2 3 3 4
i=3    ->       ↑
j=9    ->                   ↑
if (3!=4)✅
    Vector -> 0 1 2 3 1 2 2 3 3 4 
    i=4    ->         ↑
    nums[i] = nums[j]
    nums[4] = nums[9]
        1   =    4
    Vector modified (1 is replaced with 4)
                      ↓
    Vector -> 0 1 2 3 4 2 2 3 3 4
----------------------------------------
For Loop Stop
----------------------------------------

Answer
Vector -> 0 1 2 3 4 2 2 3 3 4
return i+1 = 5
```

%%[links]