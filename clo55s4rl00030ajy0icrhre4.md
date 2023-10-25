---
title: "Koko Eating Bananas - Leetcode 875"
datePublished: Wed Oct 25 2023 02:51:03 GMT+0000 (Coordinated Universal Time)
cuid: clo55s4rl00030ajy0icrhre4
slug: leetcode-0875
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698202200992/4ad4b988-cbdc-498e-ae70-eaa23ff0bbab.jpeg
tags: go, leetcode

---

Koko loves to eat bananas. There are `n` piles of bananas, the `i<sup>th</sup>` pile has `piles[i]` bananas. The guards have gone and will come back in `h` hours.

Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return *the minimum integer* `k` *such that she can eat all the bananas within* `h`*hours*.

 **Example 1:**

```plaintext
Input: piles = [3,6,7,11], h = 8
Output: 4
```

**Example 2:**

```plaintext
Input: piles = [30,11,23,4,20], h = 5
Output: 30
```

**Example 3:**

```plaintext
Input: piles = [30,11,23,4,20], h = 6
Output: 23
```

 **Constraints:**

* `1 <= piles.length <= 10<sup>4</sup>`
    
* `piles.length <= h <= 10<sup>9</sup>`
    
* `1 <= piles[i] <= 10<sup>9</sup>`
    

# Solution in Golang

```go
func minEatingSpeed(piles []int, h int) int {
  lo, hi, ans := 1, 1000000000, 1
  for lo <= hi {
    mid := (lo + hi) / 2
    if canEat(piles, h, mid){
      ans = mid 
      hi = mid -1 
    }else {
      lo = mid +1
    }
  }
  return ans 
}

func canEat(pile []int, timeLimit, speed int )bool {
  timeNeed := 0
  for _, banana := range pile {
    timeNeed = timeNeed + (banana + speed - 1) / speed
    if timeNeed > timeLimit {
      return false
    }
  }
  return true
}
```

This code is a Go implementation for finding the minimum eating speed required to eat all the bananas within a given time limit. The function `minEatingSpeed` takes in two parameters: `piles`, which is an array of integers representing the number of bananas in each pile, and `h`, which represents the time limit in hours.

The function initializes three variables: `lo`, `hi`, and `ans`. The `lo` and `hi` represents the lower and upper bounds for the eating speed, while `ans` stores the final answer. The function uses a binary search approach to find the minimum eating speed. It starts by setting `lo` to 1 and `hi` to a large number, here 1000000000.

The code then enters a while loop that runs until `lo` is less than or equal to `hi`. Inside the loop, it calculates the middle value `mid` using the formula `(lo + hi) / 2`. Then it calls the `canEat` function, passing in the `piles`, the time limit `h`, and the current eating speed `mid`.

If the `canEat` function returns true, it means it's possible to eat all the bananas within the given time limit using the current speed. In this case, the function updates the `ans` to the current `mid` value, indicating a possible minimum speed, and adjusts `hi` to `mid - 1` to search for smaller values.

If the `canEat` function returns false, it means it's not possible to eat all the bananas within the time limit at the current speed. In this case, the function updates `lo` to `mid + 1` to search for higher values.

The `canEat` function calculates the total time needed to eat all the bananas using the current speed. It iterates through each pile of bananas, calculates the time required for each pile at the given speed, and adds it to the total time. If the total time exceeds the given time limit, the function returns false. Otherwise, it returns true.

Finally, the `minEatingSpeed` function returns the final `ans`, which represents the minimum eating speed required to eat all the bananas within the given time limit.