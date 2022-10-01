# Implicit Type Coercion

- When does implicit type coercion happen?
    - It happens when an operation involves values of two different types and JavaScript coerces the values so that they have the same type.
- How is non-strict equality `==` operators different from strict equality `===` operator?
    - They both work identically as long as its operands have the same type, but if the type is different the `===` strict equality operator returns `false`, where as `==` non strict equality operator implicitly coerces the values to have the same type and then compares them.
    - What happens when we compare string values with numbers using `==` loose equality operator?
        - JavaScript implicitly coerces the string literal into a number literal. And then compares them, if they are equal it returns `true` otherwise it returns `false`.
    - What happens when you compare boolean with numbers using  `==` loose equality operator?
        - When comparing a boolean with any value, `==` coerces `true` and `false` to their number equivalent which are `1` and `0` respectively.
    - What happens when you compare a boolean with a string using  `==` loose equality operator i.e. `true == '1'` ?
        - First the boolean literal is coerced into a number. Then the comparison becomes `1 == '1'`. Now when ever we compare a string with a number the string is coerced into number by the `==` operator. After coercion the comparison becomes `1 == 1`, which evaluates as true.
- What happens when we compare `undefind` and `null` using loose equality operator?
    - It evaluates as true.
- How does `==` behaves when the operands are objects?
    - When both operands are objects `==` behaves as `===` operator, that is it considers two objects equal only when they’re the same objects. i.e. they occupy the same location in memory
    
    ```jsx
    > let arr = []
    > arr = []
    false
    > arr == arr
    true
    ```
    
- How does `==` behave when one of the operands is an object type and the other is a primitive type?
    - `==` coerces the object into a primitive before making a comparison.
    - If it’s a plain object then it will be coerced into a string i.e. `'[object Object]'`.
    - If its an empty array then it will be coerced into an empty string.

```jsx
>[] == 0
```

- what does the above expression evaluate to?
    - The array is coerced into an empty string `''`, and then compared with `0` i.e. `'' == 0`, now when the comparison is between a string and a number, `==` coerces the string into a number, i.e. `0 == 0`, empty string is converted to `0`.Thus the above expression evaluates to `true`.l

---

- What happens when a string is compared with number?
    - The string is coerced into a number.
- What happens when a boolean is compared with any other value?
    - The boolean value is coerced into a number i.e. `true` is coerced to `1` and `false` is coerced to `0`.
- What happens when an object is compared with a primitive value?
    - The object is coerced into a string i.e. `[object Object]`. Then it’s compared again using `==`.
- What happens when we compare `null` and `undefined` using `==`?
    - It evaluates as true.
- What happens when one of the operands of `+` operator is a string and the other is a number i.e. `'number' + 1`?
    - The general rule is that whenever one of the operands of the `+` operator is a string, the other operand is coerced into a string and concatenated with the string.

```jsx
> '' + [1, 2, 3]
'1,2,3'
> '' + true
'true'
> '' + undefined
'undefined'
> '' + {}
'[object Object]'
```

- Explain What all of the above expression evaluate to?
    - `'' + [1, 2, 3]`, when one of the operands of `+` operator is a string then the other operand is coerced into a string first and then concatenated with the string. i.e. `[1,2,3]` is coerced into a string `'1,2,3'` and then concatenated with the empty string `''`.
    - `'' + true`, true is coerced into a string `'true'` and then concatenated with the empty string.
    - 
    

```jsx
> 1 + true
> 1 + false
> true + false
> null + false
> null + null
> 1 + undeinfed

```

- What happens when both operands to the `+` operator are a combination of numbers, booleans, `null` s or `undeinfed`s?
    - They are converted to numbers and added together.
- What happens when one of the operands of the `+` operator is an object?
    - Both operands are converted into strings and concatenated together.
    
    ```jsx
    > [1] + 2
    '12'
    > [1,2] + 3
    '1,23'
    > 42 + {}
    '42[object Object]'
    ```
    

- What happens when comparing two operands using relational operators i.e. `<`, `>`, `<=`, `>=` ?
    - If the two operands are strings then JavaScript compares them in lexicographic order, otherwise it converts both into numbers before comparing them.
    
    ```jsx
    > 11 > '9' //--string '9' is coerced into a number and then compared with 11
    > 123 > 'a' //-- the string is converted to a number but the conversion returns NaN because the string contains a non-numerical character
    > true > null// -- true is coerced into number 1 and null is coerced into number 0
    > undefined > 1// undefined is converted into a number which returns NaN
    ```