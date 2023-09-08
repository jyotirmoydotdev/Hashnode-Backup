---
title: "Min Stack - Leetcode 155"
datePublished: Fri Sep 08 2023 18:22:37 GMT+0000 (Coordinated Universal Time)
cuid: clmaxd3fk000609ie3ho449m6
slug: leetcode-0155
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694197276932/1decd23e-1ec2-45a5-a3fb-ca006cb4aa2f.jpeg
tags: go, leetcode

---

# Problem - Leetcode

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the `MinStack` class:

* `MinStack()` initializes the stack object.
    
* `void push(int val)` pushes the element `val` onto the stack.
    
* `void pop()` removes the element on the top of the stack.
    
* `int top()` gets the top element of the stack.
    
* `int getMin()` retrieves the minimum element in the stack.
    

You must implement a solution with `O(1)` time complexity for each function.

**Example 1:**

```go
Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]

Explanation
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2
```

**Constraints:**

* `-2<sup>31</sup> <= val <= 2<sup>31</sup> - 1`
    
* Methods `pop`, `top` and `getMin` operations will always be called on **non-empty** stacks.
    
* At most `3 * 10<sup>4</sup>` Calls will be made to `push`, `pop`, `top`, and `getMin`.
    

# Solution in Golang

```go
type MinStack struct {
	stack    []int
	minStack []int
}
func Constructor() MinStack {
	return MinStack{}
}
func (this *MinStack) Push(val int) {
	this.stack = append(this.stack, val)
	if len(this.minStack) == 0 || val <= this.minStack[len(this.minStack)-1] {
		this.minStack = append(this.minStack, val)
	}
}
func (this *MinStack) Pop() {
	if this.isEmpty() {
		return
	}
	popped := this.stack[len(this.stack)-1]
	this.stack = this.stack[:len(this.stack)-1]
	if popped == this.minStack[len(this.minStack)-1] {
		this.minStack = this.minStack[:len(this.minStack)-1]
	}
}
func (this *MinStack) Top() int {
	if this.isEmpty() {
		return 0
	}
	return this.stack[len(this.stack)-1]
}
func (this *MinStack) GetMin() int {
	if this.isEmpty() {
		return 0
	}
	return this.minStack[len(this.minStack)-1]
}
func (this *MinStack) Len() int {
	return len(this.stack)
}
func (this *MinStack) isEmpty() bool {
	return this.Len() == 0
}
```

This code defines a data structure called `MinStack` is designed to support efficient retrieval of the minimum element in a stack of integers. It uses two stacks, `stack` and `minStack`, to achieve this functionality.

Here's a detailed explanation of each part of the code:

1. `type MinStack struct`: This line defines a struct named `MinStack`, which contains two fields:
    
    * `stack`: This field is a slice (dynamic array) that will store the elements of the main stack.
        
    * `minStack`: This field is another slice that will store the minimum elements encountered so far in the main stack.
        
2. `func Constructor() MinStack`: This is a constructor function that initializes and returns an instance of the `MinStack` struct. It simply returns an empty `MinStack` by calling `MinStack{}`.
    
3. `func (this *MinStack) Push(val int)`: This method is used to push an integer value `val` onto the main stack. It does the following:
    
    * Appends `val` to the `stack`.
        
    * Checks if `minStack` is empty or if `val` is less than or equal to the current minimum value stored in `minStack`. If true, it also appends `val` to `minStack`.
        
4. `func (this *MinStack) Pop()`: This method is used to pop the top element from the main stack. It does the following:
    
    * Check if the main stack is empty (using the `isEmpty()` helper method) and returns if it is.
        
    * Pops the top element from the `stack`.
        
    * Check if the popped element is equal to the current minimum value stored in `minStack`. If true, it also pops the top element from `minStack`.
        
5. `func (this *MinStack) Top() int`: This method returns the top element of the main stack without removing it. It checks if the stack is empty and returns 0 if it is.
    
6. `func (this *MinStack) GetMin() int`: This method returns the current minimum element in the main stack (the top element of `minStack`). It also checks if the stack is empty and returns 0 if it is.
    
7. `func (this *MinStack) Len() int`: This method returns the length (number of elements) of the main stack.
    
8. `func (this *MinStack) isEmpty() bool`: This is a helper method that checks if the main stack is empty by comparing its length to 0. It returns `true` if the stack is empty, `false` otherwise.
    

In summary, this code defines a specialized stack data structure that maintains two stacks: one for the main stack and another for keeping track of the minimum element. This allows for efficient retrieval of the minimum element in constant time while supporting standard stack operations like push and pop.