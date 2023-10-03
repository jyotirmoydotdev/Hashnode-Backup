---
title: "Car Fleet - Leetcode 853"
datePublished: Tue Oct 03 2023 14:25:45 GMT+0000 (Coordinated Universal Time)
cuid: clnaewsg9000g09ia7ex031d7
slug: leetcode-0853
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696342854768/a424d722-495a-4ca9-a5ba-2e128caeb645.jpeg
tags: go, leetcode

---

# Problem - Leetcode

There are `n` cars going to the same destination along a one-lane road. The destination is `target`miles away.

You are given two integer array `position` and `speed`, both of length `n`, where `position[i]` is the position of the `i<sup>th</sup>` car and `speed[i]` is the speed of the `i<sup>th</sup>` car (in miles per hour).

A car can never pass another car ahead of it, but it can catch up to it and drive bumper to bumper **at the same speed**. The faster car will **slow down** to match the slower car's speed. The distance between these two cars is ignored (i.e., they are assumed to have the same position).

A **car fleet** is some non-empty set of cars driving at the same position and same speed. Note that a single car is also a car fleet.

If a car catches up to a car fleet right at the destination point, it will still be considered as one car fleet.

Return *the* ***number of car fleets*** *that will arrive at the destination*.

**Example 1:**

```go
Input: target = 12, position = [10,8,0,5,3], speed = [2,4,1,1,3]
Output: 3
Explanation:
The cars starting at 10 (speed 2) and 8 (speed 4) become a fleet, meeting each other at 12.
The car starting at 0 does not catch up to any other car, so it is a fleet by itself.
The cars starting at 5 (speed 1) and 3 (speed 3) become a fleet, meeting each other at 6. The fleet moves at speed 1 until it reaches target.
Note that no other cars meet these fleets before the destination, so the answer is 3.
```

**Example 2:**

```go
Input: target = 10, position = [3], speed = [3]
Output: 1
Explanation: There is only one car, hence there is only one fleet.
```

**Example 3:**

```go
Input: target = 100, position = [0,2,4], speed = [4,2,1]
Output: 1
Explanation:
The cars starting at 0 (speed 4) and 2 (speed 2) become a fleet, meeting each other at 4. The fleet moves at speed 2.
Then, the fleet (speed 2) and the car starting at 4 (speed 1) become one fleet, meeting each other at 6. The fleet moves at speed 1 until it reaches target.
```

**Constraints:**

* `n == position.length == speed.length`
    
* `1 <= n <= 10<sup>5</sup>`
    
* `0 < target <= 10<sup>6</sup>`
    
* `0 <= position[i] < target`
    
* All the values of `position` are **unique**.
    
* `0 < speed[i] <= 10<sup>6</sup>`
    

# Solution in Golang

```go
func carFleet(target int, position []int, speed []int) int {
	pair := make([]carInfo, 0, len(position))
	stack := make([]float32, 0, len(position))
	for i, _ := range position {
		pair = append(pair, carInfo{position[i], speed[i]})
	}
	sort.Slice(pair, func(i, j int) bool {
		return pair[i].pos < pair[j].pos
	})
	for i := len(pair) - 1; i >= 0; i-- {
		stack = append(stack, float32(target-pair[i].pos)/float32(pair[i].spd))
		if len(stack) >= 2 && stack[len(stack)-1] <= stack[len(stack)-2] {
			stack = stack[:len(stack)-1]
		}
	}
	return len(stack)
}

type carInfo struct {
	pos int
	spd int
}
```

This Go code defines a function `carFleet` calculates the number of car fleets that can reach a target destination. Let me break down the code step by step:

1. `func carFleet(target int, position []int, speed []int) int`: This is the function definition. It takes three parameters: `target`, which is the target destination, `position`, which is a slice of integers representing the initial positions of cars, and `speed`, which is a slice of integers representing the speeds of cars.
    
2. `pair := make([]carInfo, 0, len(position))`: Here, a slice named `pair` is created to store car information. It's initially empty but has a capacity equal to the length of the `position` slice.
    
3. `stack := make([]float32, 0, len(position))`: Another slice named `stack` is created, which will be used to store the time it takes for each car to reach the target. It's initially empty but has a capacity equal to the length of the `position` slice.
    
4. `for i, _ := range position { pair = append(pair, carInfo{position[i], speed[i]}) }`: This loop iterates over the `position` and `speed` slices and populates the `pair` slice with `carInfo` structures. Each structure stores the position and speed of a car.
    
5. `sort.Slice(pair, func(i, j int) bool { return pair[i].pos < pair[j].pos })`: The `pair` slice is sorted based on the car positions in ascending order using the `sort.Slice` function.
    
6. The next loop iterates over the sorted `pair` slice in reverse order (from the car closest to the target to the car farthest from the target).
    
7. `stack = append(stack, float32(target-pair[i].pos)/float32(pair[i].spd))`: For each car, it calculates the time it takes to reach the target using the formula `(target - position) / speed` and appends this time to the `stack` slice.
    
8. `if len(stack) >= 2 && stack[len(stack)-1] <= stack[len(stack)-2] { stack = stack[:len(stack)-1] }`: If the `stack` contains at least two elements and the time for the current car is less than or equal to the time for the previous car, it means the current car will catch up to the previous car in a fleet. In this case, the previous car's time is removed from the `stack`.
    
9. Finally, the function returns `len(stack)`, which represents the number of car fleets that can reach the target without colliding.
    

The code leverages sorting and a stack-like approach to efficiently calculate the number of car fleets that can reach the target without collisions.