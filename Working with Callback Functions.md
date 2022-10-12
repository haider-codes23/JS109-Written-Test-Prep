# Working with Callback Functions

- Why are JavaScript Functions referred to as ?
    - Javascript functions are referred to as **First Class Functions.**
    - What are First class functions ?
        - They can be assigned to a variable or to an element of a data-structure such as arrays and objects.
        - They can be passed as arguments to other functions
        - They can be returned as a return value of a function
- What are Higher order functions ?
    - Functions that take other functions as argument are called higher order function, as are functions that return other functions.

---

```jsx
[[1, 2], [3, 4]].forEach(arr => console.log(arr[0]));
// 1
// 3
// => undefined
```

- Explain the code above with precision ?
    - First we notice that we’re calling `forEach` with a callback function that means that `forEach` is a higher order function. We use a multi-dimensional array to call `forEach`. Each inner array is passed to the callback function, in turn, and assigned to the parameter `arr` of the callback function. We then use the element reference operator `[]`, to get the value at index `0` of the array. On the first invocation of the callback, `arr[0]` returns the `1` and on the second it returns `3`. In each invocation `console.log` outputs a string representation of the value returned by `arr[0]`. Since its a single statement callback, the callbacks return values is the return value of `console.log(arr[0])` which is `undefined`. `forEach` doesn’t do anything with that returned value though. Finally no matter what the callback returns, `forEach` always returns `undefined`.
    
    | Action | Performed on | Side Effect  | Return value | Is return value used? |
    | --- | --- | --- | --- | --- |
    | method call forEach | outer array | none | undeined | no |
    | callback execution | Each sub-array | none | undefined | no |
    | element reference [0] | Each sub-array | none | Element at index 0 of each sub-array | yes, used  by console.log |
    | method call console.log | Element at index 0 of the sub-array | Outputs string representation of a number | undefined | yes, used to determine callback’s return value |

```jsx
[[1, 2], [3, 4]].map(arr => console.log(arr[0]));
// 1
// 3
// => [undefined, undefined]
```

- Explain the code above with precision?
    - The first thing to notice is that we are invoking `map` method on a multi-dimensional array with a callback function as argument. That means `map` method is a higher order function. Each inner array is passed to the callback as an argument, in turn, and assigned to the parameter `arr`. We then use element reference operator `[]` to get the values at index `0` of the array. On the first invocation it returns `1` and on second it returns `3`. In each invocation `console.log` outputs the value returned by `arr[0]`. Since it’s a single statement callback the return value of the callback is the return value of `console.log` which is `undefined`. `map` method uses the return value of the callback to determine it’s own return value. `map` method returns a new array that contains one element for each element of the array that invoked the `map` method, with each element set to the return value of the callback function. On all two invocation of the callback function, it returns `[undefined`.In](http://undefined.In) the end  `map`method returns an array that contains two element both having the value `undefined`.
    
    | Action | Performed on | Side Effect  | Return value | Is return value used? |
    | --- | --- | --- | --- | --- |
    | method call map | the outer array | None | [undefined, undefined,] | No |
    | callback execution | Each sub-array | None | undefined  | yes, map method uses for transformation  |
    | element reference [0] | Each sub-array | None | returns the element at index 0 of each sub-array | yes, by the console.log  |
    | method call console.log | Element at index 0 of each sub-array | Outputs a string representation of the number. | undefined | yes, as the return value of the callback function |

```jsx
[[1, 2], [3, 4]].map(arr => {
  console.log(arr[0]);
  return arr[0];
});
```

- Explain the code above with precision ?
    - The first thing to notice is that we are invoking `map` method on a multi-dimensional array, with a callback function as an argument. That means `map` method is a higher order function. Each inner array is passed as an argument to the callback function, in turn, and assigned to the parameter `arr`.  We then use element reference operator `[]` to get the value at index `0` of the array. On the first invocation it return `1` and on second `3`. In each invocation `console.log` outputs the value returned by `arr[0]`. Since it’s not a single statement callback, there is an explicit return statement that returns the element at index `0` the array on each invocation of the callback. `map` method uses the callback’s return value to determine its own return value. `map` method returns a new array that contains one element for each element of the calling array, with each element set to the return value of the callback function. So one first invocation the callback returns `1` and on second it returns `3`. In the end `map` method returns an array that contains two element `[1, 3]`.
    
    | Action | Performed on | Side Effect  | Return value  | Is return value used? |
    | --- | --- | --- | --- | --- |
    | method call map | the outer array | none | [1, 3] | no |
    | callback exection | Each sub-array | none | Number at index 0 of the sub-array | yes , used by map to transform the array |
    | element reference [0] | Each sub-array | none | Element at index 0 of the sub-array | yes, used by console.log |
    | method call console.log | Element at index 0 of the sub-array | Outputs string representation of a number | undefined | no |
    | element reference [0] | Each sub-array | none | Number at index 0 of the sub-array | Yes, as the explicit return value of the callback function |

```jsx
let myArr = [[18, 7], [3, 12]].forEach(arr => {
  return arr.map(num => {
    if (num > 5) {
      return console.log(num);
    }
  });
});
```

- Explain the code above with precision ?
    - The first thing to notice is that we are calling `forEach` method with a callback function as argument, that means `forEach` method is a higher order function. We are using a multi-dimensional array to invoke the `forEach` method. Each sub-array is passed to the callback function as an argument, in turn and assigned to the parameter `arr`. Next thing to notice is that we are calling `map` method on the array passed as an argument to the callback function. `map` method then takes a callback function as argument. Each element of the array get passed to the callback function as an argument, in turn and gets assigned to the parameter `num`. In each invocation of the callback associated with `map` method, a conditional check occur e.g. if the value of `num` is greater than `5`, the block of code associated with the `if` statement is executed. On the first invocation of the inner callback it outputs `18` and on second `7` using `console.log`, since the callback function is not a single statement callback, so it uses an explicit return statement, now the return value of the callback is the return value of `console.log` which is `undefined`. `map` method uses the callback functions return value to determine it’s own return value. map method transforms an array. It returns a new array that contains one element for each element of the calling array, with each element set to the return value of the callback. So on the first invocation of the outer callback `map` method returns the array `[undefined, undefined]`
    
    | Action | Performed on | Side Effect | return value | Is return value used |
    | --- | --- | --- | --- | --- |
    | Variable declaration and initialization  | n/a | none | undefined | No |
    | method call forEach | outer array [[18, 7], [3, 12]] | None | undefined | yes, its used to initialize the variable myArr |
    | outer callback execution  | Each sub-array | None | [undefined, undefied] | No |
    | method call map | Each sub-array | None | [undefined, undefied] | Yes, returned by the outer callback |
    | inner callback execution  | Element of the sub-array in that iteration | None | undefined | yes used by map method to transform the array. |
    | comparison num > 5 | Element of the sub-array in that iteration | None | Boolean | yes , evaluated by if |
    | method call console.log | Element of the sub-array in that iteration | None | undefined | yes, used to determine the return value of inner callback |

```jsx
[[1, 2], [3, 4]].map(arr => {
  return arr.map(num => num * 2);
});
```

- Explain the code above with precision ?
    - Answer
    
    | Action | Performed on | Side Effect | Return value | Is the return value used  |
    | --- | --- | --- | --- | --- |
    | method call map | Outer array [[1, 2], [3, 4]] | none | [[2, 4], [6, 8]] | No |
    | outer callback execution | Each sub-array | none | New transformed sub-array | yes its used by top level map method to transform the array |
    | method call map | Each sub-array | none | New transformed sub-array | yes used as return values of the outer callback |
    | inner callback execution | Element of the sub-array in that iteration | none | A number | Yes by inner map method to transform sub-array |
    | num * 2 | Element of the sub-array in that iteration | none | A number | Yes, as the return values of the inner callback |
    
    ```jsx
    [{ a: 'ant', b: 'elephant' }, { c: 'cat', d: 'dog' }].filter(object => {
      return Object.keys(object).every(key => object[key][0] === key);
    });
    
    // => [ { c: 'cat', d: 'dog' } ]/
    ```
    
    - Explain the above code with precision ?
        
        
        | Action | Performed on | Side Effect  | Return value | Is return value used |
        | --- | --- | --- | --- | --- |
        | method call filter | outer array [{a: 'ant', b: 'elephant'}, {c: 'cat', d: 'dog'}] | None | [{c: 'cat', d: 'dog'}] | No |
        | outer callback execution | Each nested object in the array | None | Boolean value  | Yes, by filter method to select Element from the array that called the filter method |
        | method call Object.keys | Each nested object in the array | None | Array that contain every own keys of the object that was passed to as argument  | Yes, its used to call every method |
        | method call every | Array that contains keys of the object that called every method | None | Boolean value | Yes, its used as the return value of the outer callback function |
        | inner callback  | String values which represent keys of an object | None | Boolean | Yes, its used by every method to determine its return value |
        | object[key][0] === key | Nested object in the array in that iteration | None | Boolean | Yes, since its a single statement callback, the return values of this expression is the also the return value of the callback  |