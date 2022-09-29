# Variables

- What are **Variables**?
    - Basically Variables are **containers** that **hold information**: their purpose is to **label** and **store** **data** in **memory** so that later on that information can be used in the program.
    - Variable is simply a **named area** of a **program’s memory space** where the program can store data. Variable’s value can be changed e.g. reassigned a different value.
    - Variable names must accurately and succinctly describe the data that the variable contains.
- What does a **variable Declaration statement** do?
    - A **Variable declaration statement** tells **JavaScript Engine** to **reserve space** for a variable with a particular name. It also implicitly specifies an **initial value** for the variable which is `undefined`. Modern JavaScript uses the **`let` keyword** to **declare a variable**. Variable declaration statements always return undefined regardless of whether we provided an explicit initial value or not.
    
- What is the difference between **variable name** and **identifier**?
    - Variables names are often refereed to as **Identifiers**. In JavaScript, identifiers refer to several things e.g. **variables names declared** with `let` and `var`, **constant names declared** with `const`, **Property names of Objects**, **Function names**, **Function parameters**, **Class name**. The term variable name includes all of these identifiers except Property names of Objects. However **Property names of Global Objects** are included when discussing about variable names.
- How are **constants declared**? And how are they different from variables? What’s the **naming convention** for Constants?
    - **Constants are declared** using `const` **keyword**. Constants have an immutable binding with their values. They are different from variables because you cannot assign it a new value after initializing it otherwise it throws a type error. And when you declare a constant you have to initialize it as well otherwise it throws a syntax error.
- What is Variable scope? What is a Block? And What is not a Block?
    - A variable scope determines where it is accessible in a program. The location where you declare a variable determines its scope. In JavaScript, variables declared with `let` or `const` have block scope.
    - A block is related set of JavaScript statements and expressions between a pair of opening and closing curly braces.
    - Not everything between pair of opening and closing curly braces is technically a block. For instance the braces surrounding an object literal do not define a block. Also the braces surrounding a function body don’t define a block either. Though it is convenient to think of function bodies as blocks.

[Exercise](https://www.notion.so/Exercise-43abca833246481facb8037837e0c7c2)