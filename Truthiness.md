# Truthiness

- How does Logical operator `&&` work?
    - It evaluates an expression that contains multiple sub-expressions, and returns a value which evaluates as either `true` or `false`. It evaluates as `true` only when all sub-expressions evaluate as `true`.
- How does logical operator `||` work?
    - It evaluates an expression  that contains multiple sub-expressions, and returns a value which evaluates as either `true` or `false`. It evaluates as `true` when any one of the sub-expressions evaluate as `true`.
- Explain the behavior exhibited by logical operators `&&` and `||`?
    - Both logical operators `&&` and `||` exhibit a behavior called short-circuiting. That means JavaScript stops evaluating sub-expressions once it can determine the final value.
    - In the case of `&&` , JavaScript short-circuits when it realizes that the expression can’t be `true`; that is when it encounters the first sub-expression(from left to right) that evaluates as false.
    - In the case of `||`, JavaScript short-circuits when it realizes that the expression can’t be false; that is when at least one sub-expression evaluates as true.
- Which values does JavaScript evaluate as false?
    - empty string, 0, false, null, undefined, NaN
- what are the terms truthy and falsy used for?
    - We have used the phrase evaluates to `true`  and evaluates to `false` several times. You can also use the terms truthy and falsy for describing the nature of a value. If a value evaluates as true then we can say that the value is a truthy value, but if it evaluates as false we can say that the value is falsy. Saying that an expression returns true or false is not the same as saying that it returns a truthy or falsy value, or that it evaluates as true or false.