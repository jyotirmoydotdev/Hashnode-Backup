---
title: "Evaluate Reverse Polish Notation - Leetcode 150"
datePublished: Tue Sep 12 2023 10:31:28 GMT+0000 (Coordinated Universal Time)
cuid: clmg6alzc000109mthami28rt
slug: leetcode-0150
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694514641192/1902934a-e07c-43e5-9f6e-9677bc6cd67d.jpeg
tags: go, leetcode, leetcode-solution

---

# Problem - Leetcode

You are given an array of strings `tokens` that represent an arithmetic expression in a [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Evaluate the expression. Return *an integer that represents the value of the expression*.

**Note** that:

* The valid operators are `'+'`, `'-'`, `'*'`, and `'/'`.
    
* Each operand may be an integer or another expression.
    
* The division between two integers always **truncates toward zero**.
    
* There will not be any division by zero.
    
* The input represents a valid arithmetic expression in a reverse polish notation.
    
* The answer and all the intermediate calculations can be represented in a **32-bit** integer.
    

**Example 1:**

```go
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
```

**Example 2:**

```go
Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
```

**Example 3:**

```go
Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```

**Constraints:**

* `1 <= tokens.length <= 10<sup>4</sup>`
    
* `tokens[i]` is either an operator: `"+"`, `"-"`, `"*"`, or `"/"`, or an integer in the range `[-200, 200]`.
    

# Solution in Golang

```go
func evalRPN(tokens []string) int {
	var stack []int
	for _, val := range tokens {
		switch val {
		case "+":
			stack = append(stack, pop(&stack)+pop(&stack))
		case "-":
			a, b := pop(&stack), pop(&stack)
			stack = append(stack, b-a)
		case "*":
			stack = append(stack, pop(&stack)*pop(&stack))
		case "/":
			a, b := pop(&stack), pop(&stack)
			stack = append(stack, b/a)
		default:
			i, _ := strconv.Atoi(val)
			stack = append(stack, i)
		}
	}
	return stack[0]
}
func pop(stack *[]int) int {
	top := (*stack)[len(*stack)-1]
	*stack = (*stack)[:len(*stack)-1]
	return top
}
```

This code defines a Go function called `evalRPN` that evaluates an expression in Reverse Polish Notation (RPN) using a stack data structure. Reverse Polish Notation is a way of representing mathematical expressions in which operators come after their operands. For example, instead of writing "3 + 4," you would write "3 4 +".

Here's a detailed explanation of the code:

1. `func evalRPN(tokens []string) int`: This function takes a slice of strings called `tokens` as input and returns an integer as the result of evaluating the RPN expression.
    
2. `var stack []int`: This line declares an empty integer stack, which will be used to store the operands as the expression is evaluated.
    
3. The code then iterates through each token in the `tokens` slice using a `for` loop:
    
    * `for _, val := range tokens {`: This loop iterates over each element (`val`) in the `tokens` slice, where `_` is used to ignore the index.
        
4. Inside the loop, there is a `switch` statement that examines the current token `val`:
    
    * `case "+":`: If the token is "+" (addition), it pops the top two values from the stack, adds them, and pushes the result back onto the stack.
        
    * `case "-":`: If the token is "-" (subtraction), it pops the top two values from the stack, subtracts the first popped value from the second popped value, and pushes the result back onto the stack.
        
    * `case "*":`: If the token is "\*" (multiplication), it pops the top two values from the stack, multiplies them, and pushes the result back onto the stack.
        
    * `case "/":`: If the token is "/" (division), it pops the top two values from the stack, divides the second popped value by the first popped value, and pushes the result back onto the stack.
        
    * `default:`: If the token is not an operator (i.e., it's a number), it converts the token to an integer using `strconv.Atoi(val)` and pushes it onto the stack.
        
5. The loop continues until all tokens have been processed.
    
6. Finally, after processing all tokens, the result of the expression is stored at the top of the stack, and it is returned as `stack[0]`. The stack should contain only one element, which is the final result of the RPN expression.
    
7. The `pop` function is defined to remove and return the top element from the stack. It takes a pointer to the stack (`stack *[]int`) and performs the necessary operations to pop the top element. It's used within the `evalRPN` function to manage the stack.
    

In summary, this code evaluates an RPN expression by processing each token one by one, using a stack to keep track of operands and intermediate results. It supports basic arithmetic operations like addition, subtraction, multiplication, and division.