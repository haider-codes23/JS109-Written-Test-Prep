# Pass by reference vs Pass by value

- What does Pass by value mean?
    - It means when you use a variable to pass an argument to a function invocation, the function can’t do anything to that sets the original variable to a different value.
    - When you pass primitive values to functions, you can treat JavaScript as Pass by value. No operation on primitive value can alter the value.
- What does by pass by reference mean?
    - It means when you use a variable to pass an argument to a function invocation, and that function does something that mutates the original variable.
    - When you pass an array or an object to a function invocation, JavaScript exhibits a combination of behaviors from both pass by value and pass by reference. Some people call it pass-by-value-of-the-reference.
    - Whether the function mutates the object that was passed to it as an argument depends on operation that’s performed on the object within the function. Some operation like the array methods `push` and `pop` are **destructive**, they permanently mutate the array. But some methods like `mapf`, `filter` and `concat`do not mutate the original object that invoked them instead return a new array.
    
    ```jsx
    function addName(arr, name) {
    	arr.push(name); // destructive method
    }
    
    let name = ["bob", "kim"];
    addName(name, "jim");
    console.log(names); //['bob', 'kim', 'jim']
    //******************************
    function addName(arr, name) {
    	arr = arr.concat([name]);
    }
    
    let names = "bob", "kim"];
    addNames(names. "jim");
    console.log(names); // ["bob", "kim"]
    
    ```
    

- Are values returned by functions also pass by value or pass by reference? Give examples
    
    ```jsx
    function foo(number) {
    	return number;
    }
    
    let number = 1;
    let newNumber = foo(number);
    console.log(number); // 1
    console.log(newNumber); //1
    
    number = 3;
    console.log(number);// 3
    console.log(newNumber); // 1
    ```
    
    - with the `foo` function we’re passing a primitive value into the function. As with all primitive values, the value is passed by value, so `foo` receives a copy of the original value. It then returns the value of the argument it received, which is yet another new value. When all that code runs, both `number` and `newNumber` have a value of `1`but the two variables are not linked in any way.
    
    ```jsx
    function bar(array) {
      return array;
    }
    
    let array = [1, 2, 3];
    let newArray = bar(array);
    console.log(array === newArray); // true (they are same object)
    
    array.push(4);
    console.log(array);    // [ 1, 2, 3, 4 ]
    console.log(newArray); // [ 1, 2, 3, 4 ]
    ```
    
    - In the `bar` function, we’re passing an array into the function. `bar` receives a pointer to the array. It then returns another reference to the same array to the calling code. When all is done both `array` and `newArray` point to the same array in memory.
- Are Assignments pass by value and pass by reference?
    - Assignments work a lot like pass by value and pass by reference and the similarity is a useful mental model, however it’s incorrect to speak of assignments in terms of pass by value and pass by reference. These terms only apply when calling and returning from a function.