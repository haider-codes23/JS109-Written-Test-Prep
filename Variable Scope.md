# Variable Scope

# Variable scope is the part of a program that can access that variable by name.

- How many types of variables are there?
    - There are two types, Global and local Variables.
    - What are global variables?
        - variables that are available across your program. You can use them anywhere in the program, either globally or inside a function or a block.
    - How many forms does local scope come in?
        - It comes in two forms: function scope and block scope.
        - Explain the rules of function scope?
            - There are a total of five rules
            - Rule 1: Outer scope variables can be accessed by inner scope.
            
            ```jsx
            1 let a = 1; // outer scope variables 
            2
            3 function logA() {
            4  console.log(a); 
            5  a += 1;// a is reassigned to a new value
            6 }
            7
            8
            9 logA();
            10 console.log(a);
            ```
            
            - What does the above code demonstrate?
                - It demonstrates two things. The first is that inner scope can access outer scoped variables. The second and less intuitive concept that it demonstrates is that you can change variable’s value from an inner scope and have that change affect the outer scope. For example, when we reassign the variable `a` in the inner scope with `a += 1`, that reassignment was visible in the outer scope when we log the value of `a`  to the console.
            - Rule 2: Inner scope variables cannot be accessed in outer scope.
            
            ```jsx
            function aFunc() {
            	let a = 1;
            }
            
            aFunc();
            console.log(a) // ReferenceError: a is not defined
            ```
            
            - What does the above code demonstrate?
                - Here the variable `a` is declared in an inner scope and when its accessed from the outer scope which is the global scope it raises a reference error and this demonstrates that inner scope variables cannot be accessed in outer scope.
                - When do local variables defined inside a function come into existence?
                    - Local variables defined inside functions only come into existence when that function is invoked. The mere act of defining a function doesn’t create any variables. The function declaration does define the scope of the variable. And once the function finishes execution these local variables are immediately discarded and control returns to the main flow of the program.
            - what is rule number 3?
                - Peer scopes do not conflict.
                
                ```jsx
                1 function funcA() {
                2 	let a = 'hello';
                3 	console.log(a);
                4 }
                5
                6 function funcB() {
                7 	console.log(a);
                8 }
                9
                9  funcA();
                10 funcB();
                ```
                
                - What does the above code demonstrate?
                    - When the code on `line 7` is executed, it throws an error since `a` is not in the scope of `funcB`. The declaration on `line 2` does declare a variable named `a` but that variable’s scope is confined to `funcA`. That also means we can declare a separate `a` variable in `funcB`. The two variables `a` would have different local scopes and would be independent of each other.
            - What is rule number 4?
                - Nested function have their own variable scope.
                
                ```jsx
                1 let a = 1;
                2
                3 function foo() {
                4   let b = 2;
                5   
                6   function bar() {
                7     let c = 3;  
                8     console.log(a);
                9     console.log(b);
                10    console.log(c);
                11  }
                12
                13   bar();
                14   
                15   console.log(a);
                16   console.log(b);
                17   console.log(c);
                18 }
                19
                20 foo();
                ```
                
                - What does the above code demonstrate?
                    - In the code above we have three levels of scope. On `line 1` we declared a variable `a` and initialized it with a number literal `2`. This variable is declared at the first level which happens to be the global scope as well. This variable `a` will be accessible throughout the program because the 1st rule of function scope says that outer scope variables can be accessed from inner scope.
                    - Then on `line 4` we declare a variable `b` inside `foo()`. This variable is declared at 2nd level and has local scope. Variable `b` cannot be accessed from the first level(Global scope) because the 2nd rule of function scope specifies that variables in inner scope cannot be accessed from an outer scope. It can only be accessed from inside the `foo()` function.
                    - Then on `line 7` we declare another variable `c` inside function `bar()`. Any variable declared inside `bar()` will have its scope confined within the function `bar()`.This variable is declared on the 3rd level. It cannot be accessed from the outer scope which includes the global scope(level 1) and scope of function `foo()` at level 2.
                    - When we call the function `foo()`, it invokes the function `bar()` which logs the value of variable `a`, `b` and `c` to the console. After `bar()` has finished execution the control returns to the main flow of the program. Then we log the value of variable `a`, `b` and `c` from inside the `foo()` function’s scope. Variable `a` can be accessed from anywhere in the the program as its scope is global, variable `b` can only be accessed from inside the function `foo()` which also includes the inner scope created by function `bar()`. When `line 17` is executed it throws a reference error that c is not defined since variable `c` is not accessible from outside scope, this also demonstrates that inner scope variables cannot be accessed from outside scope. t
                    
                - What is the 5th rule of function scoping?
                    - Inner scope variables can shadow outer scope variables.
                    
                    ```jsx
                    1 let number = 10;
                    2
                    3 [1, 2, 3].forEach(number => {
                    4 	console.log(number);
                    5 });
                    ```
                    
                    - Explain the above code with respect to the 5th rule of function scope?
                        - Here on `line 1` we have a variable named `number` in the outer scope. Then on line 3 inside the `forEach` method we have a parameter with the same name as that of the variable on `line 1` `number`. Now when `forEach` method is executed it uses the parameters to store the value of the element that `forEach` is iterating over and we also know that inner scope has access to outer scoped variables, so we’d have two local variables in the inner scope with the same name. When that happens, it’s called variable shadowing, it prevents access to the outer scope variables. The `console.log(number)` uses the parameter `number` and discards the outer scoped local variable. Variable shadowing also prevents us from making changes to the outer scoped `number`
                        - Whenever you have one scope nested within another, variables in the inner scope will shadow variables in the outer scope having the same name. i.e.
                        
                        ```jsx
                        1 let a = 1;
                        2 
                        3 function doIt(a) {
                        4   console.log(a);
                        5 }
                        6 
                        7 doIt(3);
                        8 console.log(a);
                        ```
                        
                        - Explain the code above?
                            - On `line 1` we have a variable named `a`. On `line 3` parameter of the function `doIt` has the same name as that of the variable declared on `line 1`. Now when we invoke the function `doIt` and pass it the value `3` as an argument, a local variable is created with the same name as that of the global variable `a`. Now when the statement on `line 4` `console.log(a)`is executed there are two variables with the name `a` that are in scope, i.e. the variable `a` in the outer scope is accessible from the inner scope and the parameter `a`.When that happens its called variable shadowing, and it prevents access to outer scoped global variable `a`. So the `console.log(a)` will use the parameter `a` and discard the outer scoped global variable. It also prevents us from making changes to the outer scoped variable `a`.
                            - When `line 8` is executed, the only variable that’s in scope is the global variable `a.`
                        
        - Explain what a block is and what are the rules for block scope?
            - blocks are segments of one or more statements and expressions grouped by opening and closing curly braces. Each braces in the construct like `if/else` and the `for` and `while` loops define new block scopes. The rules for block scope are identical to those for function scope.
            - Rule 1: outer blocks cannot access variables from inner scopes. OR inner scoped variables cannot be accessed in outer scope.
            - Rule 2: Inner blocks can access variables from outer scopes. OR Outer scope variables can be accessed by the inner scope
            - Rule 3: Variables defined in an inner block can shadow variables from outside scopes.
            
            ```jsx
            function aFunc() {
              let a = 'foo';
            
              if (true) {
                let b = 'bar';
                console.log(a); // => 'foo'
            
                if (true) {
                  let c = 'baz';
                }
            
                console.log(a); // => 'foo'
                console.log(b); // => 'bar'
                console.log(c); // => ReferenceError
              }
            
              console.log(a); // => 'foo'
              console.log(b); // ReferenceError
              console.log(c); // ReferenceError
            }
            
            aFunc();
            ```
            
            - When the function `aFunc` is invoked on the last line, and the function starts executing, it declares a variable `a` , then the first conditional expression evaluates as true and the block associated with it is executed, it declares a variable `b` and logs the value of variable `a` to the console. This demonstrates that inner blocks can access variables from outer scope. Before the first block finishes execution there is another nested conditional expression that evaluates as true and the block associated with it is executed, which declares a variable `c`. When the block finishes execution there are three `console.log()` statement from the outer block corresponding to the first `if` conditional that are executed. Variable `a` is accessible from the inner block corresponding to the first `if` statement as inner blocks can access variables from outer scope, variable `b` is in scope so its also accessible but variable `c` cannot be accessed because outer blocks cannot access variables from inner scope.