# Functions

- What are **Arguments**?
    - **Function are called/ Invoked** by typing their name with some values those values are called **Arguments**. **Arguments** lets you **pass data** from **outside the function’s scope** into the function so that it can **access the data**.
- What are **return values** and **return statements**? What are those functions called that always return a Boolean value?
    - All JavaScript **function calls** **evaluate** to a **value**. By **default** that value is **`undefined`,** it is the **implicit return value** of most JavaScript functions. However you can use an **explicit return value** using a **return statement**. A return statement returns a value to the code that called the function: the caller.
    - Functions that always return a value are called **predicates**.
- What are **Parameters**? What is the **scope of the parameters**?
    - In the **definition of a function**, the names between the parentheses are **Parameters**. The argument is the value of those parameters. Parameters are **local variables**, they are only **defined locally**, within the **body of the function**. And parameters get **initialized** when we **pass a value(Argument)** while **calling/ Invoking** a function. So **Parameter’s scope** is the **function definition.**
- How many kinds of variables are there? Which variable type are Parameters? What is block scoping?
    - There are two types of variables Global and Local variables. Global variables are available through out the program, while local variables are confined to a function or block and are not available outside the function’s body. The keyword that you use and the location where you define a variable determines the scope of the variable.
    - Parameters of a function act as local variables. Parameters have local scope within a function. Local variables are short lived; they go away when the function that corresponds to that scope go away.
    - Block scoping occurs when you use `let` or `const` to declare a variable inside a block, it confines the scope of that variable inside that block.
- What is the difference between Function Invocation and Method Invocation?
    - We call a function by typing its name followed by some values inside the parentheses. And we call this function Invocation. e.g. `functionName(parameters)` but Method Invocations have a different syntax, we prepend a variable name or value followed by a period `.` to a function invocation e.g. `'xyzy'.toUpperCase()` .
- Do Methods mutate their caller? Give Examples?
    - Yes and no. `toUpperCase()` is a method that **preserves** the previous value of the string, doesn’t mutate its caller and returns a new string value. But some methods permanently alter the object that invoked them e.g `pop()` method used on arrays. The `pop()` method removes the last element from the array, but does so destructively. `pop()` alters the array in place.
    
    ```jsx
    > let name = "haider";
    > name.toUpperCase();
    = "HAIDER"
    > name
    = "haider"
    
    > let arr = [1, 2, 3, 4, 5];
    > arr.pop();
    = 5
    > arr
    = [1, 2, 3, 4]
    
    ```
    
- Do Function mutate their arguments? Give Examples?
    - Mutation is a concern when dealing with arrays and objects, but not with Primitive values like strings, boolean, numbers. Primitive values are immutable. That means their values never change: operations on primitive values always return new values. Operations on mutable values may or may not return a new value and may or may not mutate data. E.g. If we have a function that takes an array as an argument and changes the first element of the array using the bracket notation syntax. If we called this function with an array and then tried accessing that array after the function had finished executing, we’ll find out that the array was mutated. Now if we had another function which also takes an array as an argument and uses the `concat()`method to add a new element into the array. If we try to access the array after the function had finished executing, we find out that original array that we passed to the function is still intact.  The `concat()` method creates a copy of the original array and mutates the copy and the returns that.
    
    ```jsx
    > function changeFirstElement(array){
    >   array[0] = 9;
    > }
    > let numbers = [1, 2, 3, 4];
    > changeFirstElement(numbers);
    > numbers
    = [1, 2, 3]
    
    > function addNewElement(array) {
    >   return array.concat(5);
    > }
    > let num = [1, 2, 3, 4]
    > addNewElement(array);
    = [1, 2, 3, 4, 5]
    > num
    = [1, 2, 3, 4, 5]
    ```
    
- What is function composition?
    - Function composition is a process that lets you use a function call as an argument to another function. e.g. passing the return value of a function call to `console.log()`.
- What are the three ways to define a function?
    - There are three ways to define a function
    - The first one is called **function declaration**. A notable property of function declaration is that you can call a function before declaring it. Any function definition that starts with the keyword `function` art the very beginning of the statement is a function declaration.
    - The second way to define a function is called **function expressions**. You have to declare a variable and then assign it to a function expression. Function expression includes the `function` keyword followed by parentheses which contain the parameters and then the function body. One key difference between function declaration and expression is that you cannot invoke a function expression before declaring it. Any function definition that doesn’t have the keyword `function` at the very beginning of a statement is a function expression.
    - The third type is called an **arrow function**, its syntax is radically different from function declaration and expression. Firstly you have to declare a variable , then an equal to sign followed by parentheses and then the arrow and at last the function body. Between the parentheses we can define our parameters for the function. And if and only if the body of the function contains a single expression we can omit the return statement.
    
    ```jsx
    // Function Declaration Example 
    functionName(para);
    // This is a function declaration
    function functionName(parameter) {
    // function body
    }
    
    // Function expression Example
    let functionName = function(parameters) {
    	//function body
    }
    ```
    
- Hang in there! Today is the tomorrow you were so worried about yesterday

[Exercise](https://www.notion.so/Exercise-bd4ffa29044441f7ab8d227e7d3c7a87)