# Flow Control

- What is a conditional and What’s the syntax used for conditionals in JavaScript? How do conditionals work?
    - **Conditional** is a fork(or multiple forks) in the road. Your data arrives at a **conditional** and it tells your data where to go. Conditionals use a combination of `**if` statements** with **comparison** and **logical operators**. The **keywords** used are **`if`** and **`else`**. Each `if` or `else` statement has a corresponding **clause**. A **clause** could be a **block** or a **statement** or an **expression**.
    - If the condition corresponding to `if` **evaluates** to `true` then the code in the `if` clause runs but if it evaluates to `false` then the code in the else clause runs. Its important to remember that the `else` clause is not a separate statement: it’s part of the `if` statement.
- What are **comparison operators** used for? Give Examples?
    - Comparison operators are used for comparing two values and it always returns a boolean value.
    - The **Strict Equality Operator `===`** also known as **Identity Operator**, returns `true` when the operands have the **same type** and **value**.
    - The **strict Inequality operator `!==`** returns `false` when the operands have the same type and value, otherwise `true`. It is the inverse of **strict equality operator.**
    - The **non-strict equality operator** `==` also known as the **loose equality operator** is similar to `===`. However, when the operands have different types, it **coerces** one the operands to the other operand’s type before it compares them, it may coerce both in some cases. The result is `true` when both values are the same and `false` otherwise. The coercion behavior can lead to **unexpected results.**
    - The **non strict inequality operator**, `!=` also known as the **loose inequality operator** is similar to `==`. However, when both **operands type** is different, it coerces one of the operands to the other operands type, in some cases it may coerce both operands. The result is `false` when both values are the same, `true` otherwise.
    - The **less than operator** `<` returns `true` when the value of the left operand is less than the value of the right operand, `false` otherwise. When comparing strings e.g `'42' < '420'`, the comparison is character by character. JavaScript moves from left to right in the strings looking for the first character that is different from its counterpart in the other string. Once it finds a character that differs, it compares that character with its counterpart, and makes a decision based on that. if both the strings are equal up to the length of the shorter string, then the shorter string is considered less that the longer string.
    - **Greater than operator** `>` returns `true` when the value of left operand is greater than the right operand, `false` otherwise.
    - **Less than or equal to operator** `<=` operator, returns `true` when the value of the left operand is less than or equal to the value of the right operand, otherwise `false`.
    
    - **Greater than or equal to operator** `>=` returns `true` when the left operand is greater than or equal to the right operand, `false` otherwise.
- What are logical Operators used for? Give Examples? And whats the return value?
    - Logical operators provide the ability to combine conditions.
    - The **not** `**!` operator** returns `true` when its operand is `false` and returns `false` when the operand is `true`. That is, it **negates** its operand. The not operator takes a single operand , the operand appears to the right of the operator. E.g. `!true` evaluates to `false` and       `!(4 === 4)` evaluates to `false`.
    - The **and operator** `&&` returns `true` when both the operands are `true` and `false` when either operand is false. E.g. `(4 === 4) && (5 === 5)` returns `true` and `(4 === 4) && (5 === 6)` returns `false`.
    - The **or operator `||`** returns `true` when either of the operand is `true` and `false` when both operands are `false`.
    - The return value is always the value of the operand evaluated last.
- What is Short Circuiting? Explain with Examples?
    - Short Circuiting is a mechanism that logical operators use to evaluate their operands. E.g. the expression `(4 === 4) && (5 === 5)` returns `true` when both the operands evaluate as `true` . If either condition is `false` then the overall result must be `false`. Thus, if the first condition is evaluated as`false` , JavaScript short circuits the entire expression by terminating evaluation, it doesn’t need to evaluate whether the second condition is `true` or `false`.
    - If we have an expression e.g. `(4 === 4) || (5 === 6)` returns `true` when either of the conditions in the expression is `true` . When either of the operand is `true` the overall result must be `true`. JavaScript short circuits the entire expression, by terminating evaluation once it determines that the first condition is true.
- What is Truthiness? Which values does JavaScript treat as `false`? Which values does JavaScript treat as `true`? What are falsy and truthy values? What is truthiness? How to coerce a truthy or falsy value to a boolean value?
    - Every `if` statement has an expression which evaluates to either `true` or `false` . However the expression doesn’t have to be a boolean value `true` or `false`. JavaScript can coerce any value to a boolean value, and that’s what it does in the conditional context like the `if` statement. So that way we can use any expression as conditional expression because JavaScript can coerce any value to a boolean value.
    - `''`, `false`, all three variations of zero(`0`, `-0`, `0n`(BigInt)) , `null`, `undefined` and `NaN`.
    - Every thing else other than the above values evaluate to `true`.
    - Values which evaluate to `false` are falsy values and values which evaluate to `true` are truthy values.
    - Truthiness is whether something is a truthy or falsy value.
    - You can use a `!!` , two consecutive not operators. The expression `!!a` is equivalent to `!(!a)`. The inner `!` converts the value of `a` to `true` if a is falsy, or `false` if `a` is truthy. The outer `!` then flips the `true` to `false` or `false` to `true`.
- What is operator precedence? How to override precedence rules?
    - Its a set of precedence rules that lets JavaScript evaluate expressions that use multiple operators and sub-expressions.
    - Operators with highest precedence are `<=`, `<`, `>`, `>=` Comparison
    - Then `===`, `!==`, `==`, `!=` Equality
    - Then `&&` Logical AND
    - Operators with lowest precedence are `||` logical OR
    - Precedence Rules could be overridden using parentheses around that part of expressions you want to be evaluated first. JavaScript evaluates parentheses in the usual algebraic order, that is it evaluates the expression in the inner most parentheses first, then works its way out. When multiple parenthesized sub-expression appear at the same depth, it evaluates them from left to right.
- What is a ternary operator and what syntax does it use? How does it work? Give Example?
    - It is a quick and easy way to write a short and concise `if/else` statement. It uses a combination of `?` and `:` symbols and takes 3 operands.                                                E.g. `1 == 1 ? 'this is true' : 'this is false'` JavaScript first evaluates the first operand (the comparison `1 == 1`. If the comparison has a truthy result, JavaScript evaluates the second operand `'this is true'` and returns its value. otherwise, it evaluates the third operand `'this is false'` and returns its value. The chief advantage ternary operator has over `if/else` statement is that the entire structure is an expression. What that means is that we can treat the ternary expressions as a value: we can assign it a variable, pass it as an argument, and so on.
- What is a switch statement? Which keywords are used for a switch statement? How does it work? why is a break statement crucial?
    - Its a **conditional flow structure** similar to an `if` statement but it has a different interface. It compares a single value with multiple values for **strict equality**.
    - It uses the keywords `switch`, `case`, `default`, and `break`.
    
    ```jsx
    let a = 5;
    switch (a) {
    	case 4:
    		console.log('a is 4');
    		break;
    	case 5:
    		console.log('a is 5');
    		break;
    	case 6:
    		console.log('a is 6');
    		break;
    	default:
    		console.log('a is some other value');
    		break;
    }
    ```
    
    - The switch statement evaluates the expression inside the parentheses, compares its value  to the value in each `case` clause and then executes the statements and expressions associated with the first matching clause. The statements and expressions in the `default:` clause run when the expression doesn’t match any of the `case` clauses.
    - break statement is crucial because when a matching `case` clause is found, and the statements and expressions associated with that case clause are executed the control will fall through to the next `case` clause and the statements and expressions associated with that `case` clause will be executed and the same thing will happen with the rest of the `case` clauses including the default `case` clause. JavaScript doesn’t care if the criteria for the extra `case` clauses doesn’t match.

[Exercise](https://www.notion.so/Exercise-e8465b850106400bac833c9be297dba2)