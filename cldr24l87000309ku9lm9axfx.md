# 9. Palindrome Number

# Question

Read the Question here [Click Here](https://leetcode.com/problems/palindrome-number/)

```bash
Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
```

# Answer

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        int oldNum=x;
        int newNum=0;
        while(0<x){
            int temp=x%10;
            newNum=newNum*10+temp;
            x=x/10;
        }
        if (oldNum==newNum){
            return true;
        }
        else{
            return false;
        } 
    }
};
```

Here we will reverse the number and check that the given number is equal to the new number. First, we need to store the old number in a variable as the variable `x` will be 0 at last, so we are using `oldNum` it as a variable to remember our given number. The variable `newNum` is where our reverse number will be stored.

Now we will use a `while` loop and check if the x is greater than 0 and run it till the x become 0. The variable `temp` store the last number of the x, eg., given the number 121 then 121%10=1, 1 is stored in the `temp` . After we get the temp then we move to the next line, here we are multiplying the `newNum` with 10 and adding the last number which we stored in temp eg., `newNum` = 0\*10+1 -&gt; `newNum` = 1 and then we will remove the last number from the `x` by dividing `x` by 10. This loop continues till the x become 0.

Till this point new will get our reverse number which is stored in, now we just need to compare this with the `oldNum`, if the number is the same then return true or else false.

```bash
Input : 121

x = 121
oldNum = 121
newNum = 0
Check if x is greater than 0 (0<121) ✅
    temp = x % 10 = 1 
    newNum = (newNum * 10) + temp = (0*10) + 1 = 0 + 1 = 1
    x = x / 10 = 121 / 10 = 12

x = 12
oldNum = 121
newNum = 1
Check if x is greater than 0 (0<12) ✅
    temp = x % 10 = 12 % 10 = 2
    newNum = (newNum * 10) + temp = (1*10) + 2 = 10 + 2 = 12
     x = x / 10 = 12 / 10 = 1

x = 1
oldNum = 121
newNum = 12
Check if x is greater than 0 (0<1) ✅
    temp = x % 10 = 1 % 10 = 1
    newNum = (newNum * 10) + temp = (12*10) + 1 = 120 + 1 = 121
    x = x / 10 = 1 / 10 = 0

x = 0
oldNum = 121
newNum = 121
Check if x is greater than 0 (0<0) ❌

check if oldNum is equal to newNum (121 == 121) ✅
    return true
```

%%[links]