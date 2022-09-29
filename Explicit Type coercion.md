# Explicit Type coercion

- What is type coercion?
    - It is the conversion of one type of value into another.
- When does Explicit coercion happen?
    - It happens when a programmer intentionally uses one of the built-in function or operators to convert one type of value into another.
- How can we convert a string type value to a number type?
    - We can use the `Number()` function which takes a string as an argument and returns a number. If it cant convert the string into a number it returns `NaN`.
    - What does `Number()` function return if we pass it an empty string or a string with white spaces ?
        - It returns `0`.
    - What does `Number()` function return if we pass it a boolean value?
        - It returns `1` if we pass it `true` and `0` if we pass it `false`.
    - What other method can we use to coerce a string into number?
        - We can use `parseInt()` function that takes a string as an argument and tries to parse an integer number from it. An unusual feature about `parseInt()` function is that it converts a string into a number even when the string contains non-numerical characters. As long as the string begins with a digit — optionally preceded by `+` or `-` it returns a number.
        - For strings that contain floating-point numbers we can use the `parseFloat()` function. It parses the numeric part of the string,and stops parsing once it finds a character that cant be part of a number.
        - We can also use the `+` operator, it’s a unary operator. It coerces a value to a number. It works like `Number()` function.
- How to coerce values to strings?
    - We can use the `toString()` method. It can be used on all JavaScript datatypes except `null` and `undefined`. JavaScript doesn’t allow to call a method on a number literal, so we either store the number literal in a variable or place it inside a pair of opening and closing parentheses followed by a `.` dot operator and then the function invocation. If you don’t want to use a variable or parentheses then use two `.` dot operators that way JavaScript doesn’t interpret the `.` after the number literal as part of the floating point number.
    - What happens if we use `toString()` method on arrays?
        - It converts every element in the array to a string, then concatenates them all with a `,` between each each character in the string. `Array.prototype.toString()` treats `null` and `undeinfed` as empty values
        
        ```jsx
        > [1, 2, 3].toString()
        '1,2,3'
        >[1, null, 2, undefined, 3].toString()
        '1,,2,,3'
        ```
        
    - What’s another way we can coerce values to Strings?
        - We can use the function `String()`. One advantage it has over `toString()` method is that it works with `null` and `undefined`.