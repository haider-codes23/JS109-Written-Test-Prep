# Side Effects

- When is a function said to have side effects?
    - If a function reassign a non-local variable. Reassigning a variable in the outer scope would be a side effect.
    - It mutates the value of any object referenced by a non-local variable.Mutating an array or object argument for instance.
    - It writes to the console log and reading from the terminal
    - It raises an exception without handling it.
    - It calls another function that has side effects.
    
    ```jsx
    function displayTotal(num1, num2) {
      console.log(num1 + num2);
    }
    ```
    
    - Does the function above have side effects and if it does explain what the side effects are?
        - Yes, it does have a side effect, it writes to the console log or outputs to the console log.
    
    ```jsx
    function append(targetArr, valueToAppend) {
      targetArr.push(valueToAppend);
      return targetArr;
    }
    ```
    
    - Does the function above have side effects and if it does explain what the side effects are?
        - Yes, it does have a side effect, it mutates the value of the array referenced by `targetArr` which was passed to the function as an argument. It mutates the an array referenced by a non-local variable.
    
    ```jsx
    function computeTotal(num1, num2) {
      return num1 + num2;
    }
    ```
    
    - Does the function above have side effects and if it does explain what the side effects are?
        - No, it doesn’t have any side effects. It just returns a useful value computed by the expression `num1 + num2`.
    
    ```jsx
    let nums = [1, 2, 3];
    function sum(numbers) {
    	let total = numbers.reduce((acc, num) => acc + num);
    	numbers.push(total);
    }
    sums(nums);
    console.log(nums)
    ```
    
    - Does the function above have side effects and if it does explain what the side effect are?
        - Yes, it does have side effects. It mutates an array referenced by the parameter `number` and the non-local variable `nums`.
    
    ```jsx
    function sum() {
    	let nums = [1, 2, 3];
    	let total = nums.reduce((acc, num) => acc + num);
    	nums.push(total);
    	return nums;
    }
    
    sum();
    ```
    
    - Does the function above have side effects and if it does explain what the side effect are?
        - No, it doesn’t have any side effects , since it doesn’t mutate a non-local variable, or an object referenced by non-local variable. Neither does it write to the console or reads from the terminal. Nor does it raise any exception without handling it.