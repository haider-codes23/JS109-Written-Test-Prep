# Nested Data Structures

# Nested Arrays within arrays

- How do you access an element in a nested array within an array?
    
    ```jsx
    let arr = [[1, 3], [2]];
    ```
    
    - Use the example above to explain your answer?
        - We’ll chain our element references together           e.g. `arr[0][1]`. The first part `arr[0]` is an element reference that returns the first element in the array which is the inner array `[1,3]` and the second part `[1]` is also an element reference that returns the second element in the inner array.

```jsx
1 let arr = [[1, 3], [2]];
2 arr[0][1] = 5;
```

- Explain the code above?
    - On `line 1` the code declares a variable `arr` and initializes it with a reference to the array `[[1, 3], [2]]` . `line 2` looks like a chained reference however it is not. The first part `arr[0]` is an element reference that returns `[1, 3]`. The second part, `[1] = 5` is the same as       `[1, 3][1] = 5` is an array element assignment, not a reference. It is an chained action, but the first part of that chain is an element reference, while the second part of that chain is element assignment.

```jsx
1 let arr = [[1], [2]];
2 arr[0].push(3);
3 arr; // => [ [ 1, 3 ], [ 2 ] ]
```

- Explain the code above on `line 2`?
    - Its a chained action which has two parts, the first one `arr[0]` is an element reference, it returns the first element which is an array `[1]`; the second could be thought of as `[1].push(3)`, which is the action that appends `3` to the end of the array.

# Nested Objects within arrays

```jsx
1 let arr = [{ a: 'ant' }, { b: 'bear' }];
2 arr[0]['c'] = 'cat';
3 arr[0].d = 'dog';
4 arr; // => [{ a: 'ant', c: 'cat', d: 'dog' }, { b: 'bear' }]
```

- Explain the code above on `line 2` and `line 3`?
    - line 2: It’s a chained action that has two part. First we have an element reference which returns the nested object `{a: 'ant'}`. Next we use the bracket notation syntax to create a new key-value pair:                          `{a: ‘ant’}[’c’] = ‘cat’`
    - line 3: It’s also a chained action, that has two parts. First we have an element reference that returns the first element in the array which is `{a: 'ant', c: 'cat'}`. Next we use dot syntax to create a new key-value pair in the object `{a: 'ant', c: 'cat'}`

```jsx
1 let a = [1, 3];
2 let b = [2];
3 let arr = [a, b];
4 arr // => [ [ 1, 3 ], [ 2 ] ]
5 a[1] = 5;
```

- What are we doing when we use variables(that point to arrays) to specify element in an array?
    - It look like we’re adding arrays to array `arr`, however we are adding references to the array `arr`.
    - What happens if we modify `a` after placing it in `arr` ,will it affect `arr`?
        - When we modify `a` on `line 5` using `a[1] = 5` it affects `arr` as well. Because `arr` contains a reference to the array `a` and changes made to the array `a` will be visible in the array `arr` as well.

# Shallow Copy

Sometimes you want to copy an entire collection to save the original collection before performing some modifications. 

### Shallow coping objects

- How can we make a copy of an array?
    - There are two ways either we can use `slice` method without any argument or we could use the ES6 spread syntax which uses `...` t expand an array to a list of values.
    
    ```jsx
    1 let arr = ['a', 'b', 'c'];
    2 let firstCopyOfArr = arr.slice();
    3 let secondCopyOfArr = [...arr];
    3 firstCopyOfArr // ['a', 'b', 'c']
    4 secondCopyArr // ['a', 'b', 'c']
    5 arr === firstCopyOfArr // false
    6 arr === secondCopyOfArr // false
    ```
    

```jsx
let arr = [['a'], ['b'], ['c']];
let copyOfArr = arr.slice();

copyOfArr[1].push('d');

arr;       // => [ [ 'a' ], [ 'b', 'd' ], [ 'c' ] ]
copyOfArr; // => [ [ 'a' ], [ 'b', 'd' ], [ 'c' ] ]
```

- What happens when we make a copy of an array that contain primitive values and nested arrays or nested Objects?
    - When we make a copy of an array that contains nested arrays and objects using `slice` method or ES6 spread syntax, it creates a shallow copy of the array: only the top level is copied. What that means is that primitive values are copied but  nested objects or arrays are shared, not copied. So if we mutate a nested array or object in the copy, it will affect the original array as well. For instance in the code above when we append a string to a nested array `['b']` in `copyOfArr`, the original array `arr` also gets mutated.
    
    ```jsx
    1 let arr = [{ a: 'foo' }, { b: 'bar' }, { c: 'baz' }];
    2 let copyOfArr = [...arr];
    3
    4 copyOfArr[1].d = 'qux';
    5
    6 arr;       // => [ { a: 'foo' }, { b: 'bar', d: 'qux' }, { c: 'baz' } ]
    7 copyOfArr; // => [ { a: 'foo' }, { b: 'bar', d: 'qux' }, { c: 'baz' } ]
    ```
    
    - Explain the code above?
        - On `line 1` we have an array `arr` that contains nested objects. On `line 2` we create a shallow copy of `arr` using the ES6 spread syntax and initialize `copyOfArr` with a reference to the copy. `line 4` can be broken down into two parts. First part `copyOfArr[1]` is an element reference which returns an object `{b: ‘bar’}`, the second part                 `{b: 'bar'}.d = 'qux'`is where we add a new key-value pair to the object `{b: 'bar'}` using dot notation syntax. Now the arrays `arr` and `copyOfArr` share a reference to the object `{b: 'bar'}` and making any changes to the nested object in `copyOfArr` will also have the same affect to the nested object `{b: ‘bar’}` in `arr`.

### Shallow copying Objects

- How can we make a copy of an object?
    - We can use `Object.assign` method to copy properties of one or more object into another. It only mutates the first object passed to it as an argument e.g. properties from the other object/ objects passed to it as arguments are added to the object passed to it as the first argument. It return the first object that was passed to it as an argument.
    - If you don’t want your object to get mutated, then you can use an empty object `{}` as the first argument.
    
    ```jsx
    let obj1 = { a: 'foo' };
    let obj2 = { b: 'bar' };
    
    Object.assign(obj1, obj2); // => { a: 'foo', b: 'bar' }
    obj1;                      // => { a: 'foo', b: 'bar' }
    ```
    
    - Explain the code above?
        - We have two objects `obj1` and `obj2` that we pass to `Object.assign` as arguments. `obj1` is the first argument and `obj2` is the second argument. Properties from `obj2` are merged into `obj1` . `obj1` get mutated and is returned in the end.

## Deep Copy

- What is a deep copy? How can we make a deep copy of an object?
    - Deep copy is an identical copy of the object and its a different object that occupies a different location in memory.
    - JavaScript doesn’t have a method or a function for deep copying but is an indirect way to do it. However it only works with nested array and objects that only have primitive, arrays and objects as elements.
    
    ```jsx
    let arr = [{ b: 'foo' }, ['bar']];
    let serializedArr = JSON.stringify(arr);
    let deepCopiedArr = JSON.parse(serializedArr);
    ```
    
    - Explain the code above?
        - `JSON.stringfy` method serializes any object including arrays that only have primitive, arrays and plain objects as elements. Serializing involves converting an object to a string form that can subsequently converted back into an identical object
        - `JSON.parse` performs that conversion from string back to an object.