# Loops and Iterating

- What are loops? What does the main structure of a loop use? What does a loop do to its body? What is iteration in the context of a loop?
    - Every program requires running a piece of code over and over again until some ending condition occurs. loops provide us this capability.
    - The main structure of a loop includes a looping keyword, an ending condition and a block.
    - A loop executes its body for as long as the condition remains truthy.
    - In the context of a loop iteration means the execution of the loops body, one iteration means executing the loop body once.
- Describe the syntax used by a `while` loop? How does the while loop work?
    - A `while` loop uses the keyword `while` followed by a conditional expression inside parentheses and a block. The loop executes the block over and over again for as long as the conditional expression is truthy.
- How is `do/while` loop different from a `while` loop?
    - A `do/while` differ visibly from a `while` loop, but there behavior are almost identical. In a `do/while` loop the conditional check occurs at the end of the loop instead of beginning, which allows it to run the code at least once, even if the condition is falsy when the loop begins.
- Describe a `for` loop? Whats the difference between a `for` loop and a `while` loop?
    - Its serves the same purpose as a `while` loop, but its syntax is condensed compared to a `while` loop. A `for` loop combines a variable initialization, a loop condition, and the variable increment/ decrement expression all on the same line.
    - The sole difference between a `while` loop and `for` loop is the scope of any variable declared by the initialization clause. In a `while` loop the scope includes the code that surrounds the loop; in a `for` loop the scope is the `for` statement and its body.
- How to control loops?
    - Loops could be controlled using `break` and `continue` statements. A `break` statement skips all the remaining iterations of a loop by terminating all the subsequent iterations. Where as, when a loop encounters a `continue` statement, it skips running the rest of the block and jumps ahead to the next iteration.
- How can we iterate over arrays without using a loop?
    - JavaScript has several array iteration methods that iterate over the elements of the array without using the looping syntax. E.g. the built-in `forEach` method.
    - What syntax does `forEach` method use?
        - Name of the array, followed by a period `.` then the method name `forEach` and at last the arguments that we pass to that `forEach` function. The most peculiar part is the argument that we pass, it’s a function definition, or to be precise, a function expression.               E.g. `namesArray.forEach(function(name){});` . The function expression doesn’t have a name thus we call it an **anonymous function.**
        - What happens when you pass a function as an argument to another function? And What happens in the context of `forEach` when we pass  it an anonymous function.
            - When you pass a function as an argument to another function, that another function can call the function represented by the argument. And that’s what `forEach` does, `forEach` loops through each element in the array, in sequence, starting from the first element. For each element of the array, `forEach` invokes the anonymous function with the element as argument.

[Exercise](https://www.notion.so/Exercise-e8fb7a8cd0b442668462d083a01859e8)