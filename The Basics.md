# The Basics

- Explain all Data Types in JavaScript with definitions ?
    - The core Job of most programming languages is dealing with **data**.
    - Data Type helps programmers and their programs determine what they can and cannot do with a given piece of **data**.
    - There are two **types** of **data** in JavaScript, **Primitive** and **Object type**
    - **Primitive** **type** includes **String**, **Number**, **Undefined,** **Null**, **boolean.**
    - Every **Type** that’s not **Primitive** is **Object Type** e.g **Array** and **plain Objects.**
    - **Data Types** values can be represented by **literals**.
    - A **literal** is any **notation** that lets you represent a fixed **value** in **source code**.
    
    ```jsx
    'Hello World' // String literal
    3.14          // Numeric literal
    true          // Boolean literal
    { a: 1, b: 2 }// Object literal
    [ 1, 2, 3 ]    // Array literal
    undefined     // Undefined literal
    ```
    
    - What are Strings?
        - **Strings** are a list of **characters** in a specific sequence.
        - **String literals** can be formed using either single or double quotes
        - Within Strings we use **backslash** ( \ ) to tell JavaScript that the subsequent character is not **syntactical**.
        - We can also use **String interpolation** **operation**, which allows us to **merge** JavaScript **expression** with strings and to form strings that include expression we use back-ticks (``) instead of single or double quotes and expression is embedded within template literals. JavaScript then replaces the **expression sub-string** with the value of the expression.  ``My name is ${nameOfPerson}!``
    - What are Numbers?
        - In JavaScript **Number type** represents all types of numbers e.g. **floating-point numbers**, and **fixed-point decimal numbers**. By all types of numbers we mean real numbers.
    - What is Boolean?
        - Boolean values represent an “on” or “off” state.
        - There are two **boolean literal values**, `true` and `false`.
    - Explain Undefined?
        - In **programming** we need a way to express the absence of value. In JavaScript, we can do that using the value `undefined`. When a **variable** is not **defined** its value is given by `undefined`.  We can also **explicitly** use the value **undefined**.
        - Or a function that doesn’t **return** any value, returns undefined e.g. `console.log`
        
        ```jsx
        
        > console.log("Hello, World")
        Helo, World
        = undefined
        
        > let name //  when we declare a varibale without giving it a value 
        = undefined
        > name // when we use this varibale it returns undefined
        = undefined
        > let personName = "Haider"
        = undefined
        > name 
        = "Haider"
        ```
        
    - Explain Null?
        - It represents the intentional absence of value. It represents **emptiness or nothing**. It is similar to undefined in their use and behavior. The main difference between them is that you have to **explicitly** use `null` if you want to use it; `undefined` can arise **implicitly**.
    - Explain typeof Operator?
        - Every Value in JavaScript has a Data Type. To find out which data type a value is we can use the `typeOf` operator. It returns a string that contains the Data type of its operands value. e.g `typeOf "haider'` would return the string `'string'` and `typeOf 6` would return the string `'number'`
    
- What basic Operations can we perform in JavaScript on numbers? Explain the concept of `NaN` and `infinity` ? And also explain the difference between `NaN` and `infinity` ? What’s the type of `NaN` and `infinity` ?
    - There are 4 operations that we can perform on numbers and they are addition, subtraction, multiplication and division. All of them require two operands. There is another operation called the remainder operation which returns the remainder of division operation. If the left hand side operand is evenly divisible by right hand side operand remainder operation returns `0`. Remainder operation returns a positive number when the first operand is positive and negative when the first operand is negative.
    - Operations, such as `0 / 0` return `NaN`, Not a Number. This special value signals an illegal operation on numbers e.g. `undefined + 0` returns `NaN` or `0 / 0` also returns `NaN` or trying to convert a non-number type e.g. `"GaryVee"` to a number will return `NaN` `Number("GaryVee")` will return the value `NaN`. Now like every other value in JavaScript has a type, `NaN`'s type is `number`. To determine whether a value is equal to `NaN`,we can’t use the comparison operator `===`,because it turns out that `NaN` is the only value in JavaScript that is not equal to itself. Instead we can use the `typeOf` operator. If we want to find out that some value is equal to `NaN` or not we can use the `Number` Object’s `isNaN()` method `Number.isNaiN()` which returns a boolean value.
    - Other operations like dividing a number by `0` returns infinity e.g `1 / 0` . Infinity has a negative counterpart, if we divide a negative number by `0` it would return negative `infinity` e.g. `-1 / 0` . Infinity is a number of infinite magnitude. `NaN` and `infinity` are two very different concepts. Infinity is a number that is to large, if i said a new number every second and kept going for the next 37 trillion years, i still won’t be able to reach infinity because there is always a larger number. Where as `NaN` is a result of an attempted mathematical operation that is neither a valid number nor an infinite number.
    
    ```jsx
    > NaN === NaN
    = false
    > typeOf NaN
    = Nan
    > Number.isNaN(3)
    = false
    > Number.isNaN(NaN)
    = true
    ```
    
    - 
- Explain what is Coercion and explicit coercion?
    - Coercion is the conversion of a value of certain data type into another data type. e.g. if you had two strings `'1'` and `'2'` and you wanted to add them mathematically and you decided to use the `+` operator it will concatenate the two values together and return `'12'` . Some how we need to coerce the strings into numbers first and then use the `+` operator to add them together. We can do this by performing explicit coercion. We can explicitly coerce a string to a number using the `Number()` function which would return us a number. The `Number()` function takes a string value as an argument and returns a number if the string is a valid numeric value. If we use a non-numeric string as an argument the `Number()` function would return the value `NaN` e.g `Number('12xyf')`.  We can also use `parseInt()` function to coerce a `string` into a `number` . It takes a string value as an argument and returns a number. If the string argument contains non-numeric characters, it stops converting the moment it encounters an invalid character and returns a number.
    - We can also convert a number into a string using the function `String()` . It takes a numeric value as an argument , any real number and returns it’s string form (only if the numeric value is valid otherwise it raises a syntax error).
- Explain what are Arrays in JavaScript?
    - Arrays in JavaScript are ordered list, they can contain any data type e.g. String, number, Boolean, null and undefined. Array literals use brackets surrounding a comma delimited list of values. Element indexes are non-negative numbers starting with `0`. And we use bracket notation to access elements in an array.
- Explain what are Objects in JavaScript?
    - It’s a **dictionary-like data structure** that **matches keys** with **specific values**. Essentially, a **JavaScript Object** is a **collection of key-value pairs**. You can create an Object using **object literals**, which have zero or more key value pairs separated by commas all embedded within **curly braces**. `e.g { dog: "barks', cat: 'meows', pig: 'oinks' }` . In arrays we used **indexes** inside **bracket notation** to **access elements** within the array, but with Object we use **key names** in **string form** inside bracket notation to access values of those keys.
- Explain what are Expressions in JavaScript?
    - An expression is anything that JavaScript can evaluate to a value, even if that value is `undefined` or `null` . Expressions evaluate to a value and also return a value.
- Explain what are Statements in JavaScript?
    - A **statement** is a line of code **commanding** a task. Every program contains a sequence of statements. Every chunk of code that can be treated as a single unit is a statement. E.g. variable, function and class declarations, loop and `if` statements, `return` and `break` statements, assignments e.g. `h = 4` and stand alone expressions e.g. `console.log("Hello")`. **Statements include expression** as a part of their **syntax**, but the statement itself is not an expression that’s why it’s value cannot be captured like that of an expression.

[Exercise](https://www.notion.so/Exercise-c2a92e384d694da4872f528da0e5523a)