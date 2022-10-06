# Exercise on Array methods(filter&map)

```jsx
[1, 2, 3].filter(num => 'hi');
```

- What does the `filter` method return and why?
    - It returns a new array `[1, 2, 3]`. `filter` method is an array iteration method. It examines the truthiness of the callbacks return value, if the callback returns a truthy value `filter` method selects that element and appends it to the new array otherwise it does not select it. In the code above the callback returns the string value `'hi'` for all three iteration which is a truthy value, so filter selects and places all three elements from the calling array into the new array. After all the iterations have completed filter returns the array of selected elements.

```jsx
[1, 2, 3].map(num => {
  num * num;
});
```

- What is the return value of `map` in the following code? and why?
    - It returns a new array `[undefined, undefined, undefined]`. `map` method is used to transform array. It returns a new array who’s elements depend on the original content of the array. It returns an array that contains one element for each element in the array, with each element set the return value of the callback function. In the code above the callback doesn’t have an explicit return value so the callback function implicitly returns the value `undefined` on all three iteration, this is why `map` returns the array  `[undefined, undefined, undefined]`.

```jsx
[1, 2, 3].map(num => num * num);
```

- What is the return value of `map` in the following code? and why?
    - `map` method looks at the return value of the callback to determine the elements in the returned array. The callback on `1st` iteration returns the value `1`, on second iteration it returns `4` and in the last iteration the callback returns `9`. `map` method appends these returned values in to a new array and returns that.
    - In an arrow function if the body contain only a single expression we can omit the return statement and arrow function returns the computed value of the expression as return value.
    

```jsx
['ant', 'bear', 'caterpillar'].pop().length;
```

- What is the return value of the following statement? Why?
    - It returns the number literal `11`. When `pop` method is invoked on the array, it destructively removes the last element, which is the string `'caterpillar'` and returns it. Then the length property of the string is accessed on the return value of `pop`.

 

```jsx
[1, 2, 3].every(num => {
  return num = num * 2;
});
```

- What is the callback's return value in the following code? Also, what is the return value of `every`
 in this code?
    - Callback’s return value is the value stored in the variable `num`. When the callback is invoked a local variable with the name `num` is created which is the parameter of the callback. This variables captures the arguments value which is passed to it by the `every` method on each iteration. Then inside the callback function’s body `num` is reassigned a new value which is equal to expression `num * 2` and at last the callback returns this new value stored in the variable `num`. e.g it returns `2`, then `4` and last `6`. The callback on each iteration returns a truthy value. And `every` method returns `true`.

```jsx
['ant', 'bear'].map(elem => {
  if (elem.length > 3) {
    return elem;
  }
});
```

- What is the return value of `map`in the following code? Why?
    - `map` returns a new array  `[undefined, 'bear']`. `map` method transform an array. It returns an array that contains one element for each element in the array, and with each element set to the return value of the callback. The callback on the 1st iteration returns `undefined` because the conditional expression in the `if` statement evaluates as false and the return statement is inside the block associated with the `if` statement, so the callback implicitly returns the value `undefined`. On the second iteration the conditional expression in the `if` statement evaluates as `true` and return statement in the `if` block is executes which returns the value `'bear'`. On each iteration `map` method append the callback’s return value to a new array and when the iterations have completed, `map` returns that array.