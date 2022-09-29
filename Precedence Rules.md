# Precedence Rules

- What is Operator precedence?
    - The meaning of an expression in JavaScript is determined by what is called operator precedence. It’s a set of rules that dictate how JavaScript determines what operands each operator takes.
    
    ```jsx
    > 3 + 5 * 7
    ```
    
    - What does the above expression evaluate to and explain why?
        - It evaluates to `38`. Precedence determines whether the `+` operator uses the `3` and `5` as operand or `3` and `35`(5 * 7). Likewise, it determines whether `*`  operator uses `5` and `7` as operands or `8`(3+ 5) and `7` as operands. In an expression an operator with higher precedence are prioritized over those with lower precedence. Operator with higher precedence than another is said to bind more tightly to its operands.  In the above expression `*` has higher precedence than `+` operator and it binds to its operands more tightly than `+` operator does, so `*` gets passed `5` and `7` as operands which returns `35` as a result. Subsequently `3` and `35` get passed to `+` for a final result of `38`.
- How can we override precedence?
    - We can use parentheses to override the **default evaluation order** and parentheses have the highest possible precedence.
- What’s another way to think about precedence?
    - Another way to think about precedence is that it **controls the order of evaluation**. Operations involving operators with high precedence get evaluated before operations involving low precedence. When two operations involve operators of same precedence, the operations occur left-to-right

```jsx
1 function value(n) {
2 console.log(n);
3 return n;
4 }
5 
6 
console.log(values(3) + value(5) * value(7));
```

- How does the code on line 6 get evaluated and what does it output? Does it get evaluated from left-to-right or does it evaluate `value(3) + value(5)` or does it does it evaluate `value(5) * value(7)`?
    - Operators like `+` and `*` need values that they can work with. Function invocations like `value(5)` and `value(7)` are not values. We can’t invoke the `*` operator until we know what values those functions return. In an arithmetic expression JavaScript goes from left to right and evaluates everything it can without calling any operators. Thus, here it evaluates `value(3)`, `value(5)` and `value(7)`first, in that order. JavaScript re-evaluates the results with the precedence rules only after it has those values.
- 
- Important Points
    - Don’t rely to much on precedence. It’s easy to forget the precedence order and get confused by an unexpected result.
    - If your’re using two or more different operators in an expression, use parentheses to explicitly define the meaning.