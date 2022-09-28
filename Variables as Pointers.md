# Variables as Pointers

- Some variables contain values while others contain pointers to an address space in memory.
- Developers some times use the term references instead of pointers, both are correct. We can say a variable points to or references an object in memory.

## Primitive types

```jsx
1 let count = 1;
2 count = 2;
```

- Explain the code above ? Explain What that looks like in the computer? Give Example?
    - On line 1 we declare a variable `count` and initialize it to value `1`. On line 2 we reassign `count` to a new primitive value `2`.
    - Every time JavaScript program creates a new variable, it causes JavaScript to allocates a spot somewhere in the memory to hold its value. With primitive values the actual value gets stored in this allocated memory.
    - The `count` variable may end up at address 0 x 1234 in the computers memory. And the memory at that address gets set to `1` and then `2`.
    
- Where do variables with primitive values store those values?
    - Variables with primitive values store those values at the memory location associated with the variable.

## Object types

```jsx
1 let obj = { a: 1};
2 obj = { b: 2};
3 obj.c = 3;
```

- Explain the code above? Explain what that looks like in the computer? Give Example?
    - On line 1 we declare a variable named `obj`, and initialize it with an object `{ a: 1 }`. Line 2 reassigns `obj` to a pointer or reference to the object `{ b: 2}`. On line 3 we mutate the object referenced by `obj` by adding a new property to the object.
    - Every time JavaScript program creates a new variable, it causes JavaScript to allocate a spot some where in the memory for the value. However with objects JavaScript doesn’t store the value of the object in the same place. Instead it allocates additional memory for the object, and places a pointer to the object in the space allocated for the variable. When we reassign `obj` on line 2 the pointer or reference to the object `{ a: 1}` stored in the memory location allocated the variable `obj`is replaced with the new pointer or reference to the object `{ b: 2}`.So the memory allocated to the variable has not changed, only thing that has changed is the pointer to the object it was storing. Now `obj` is pointing to a new memory location. Then on line 3 we mutate the object referenced by `obj` by adding a new property to the object.
    - In the above example variable `obj` may end up at the address space 0 x 1234 in the computers memory. The memory at that address get set to a pointer or reference to an object  `{ a: 1}` and then a pointer or reference to object `{ b: 2}`. And at last the object referenced by `obj` is mutated by adding a new property to the object.

```jsx
1 let c = [1, 2];
2 let d = c;
3 c = [3, 4];
4 c
5 [3, 4]
6  
7 d
8 [1, 2]
```

- Explain the code above? Explain what that looks in the computer? Give Example
    - On line 1 a variable named `c`  is declared and initialized with a pointer or reference to the array  `[1, 2]`. On line 2 a variable named `d` is declared and initialized with the value contained by variable `c` which is a pointer or reference to the array `[1, 2]`. On line 3 variable `c` is reassigned a pointer or reference to a new array.
    - Every time JavaScript program creates a new variable it causes JavaScript to allocate a spot somewhere in memory for the value. Because arrays are object and JavaScript doesn’t store the value of the object(array) in the same place. Instead it allocates additional memory for the object(array), and places a pointer to the array in the space allocated for the variable. Then on line 2 variable `d` is declared which is allocated a spot somewhere in the memory for its value. It is initialized with a the value of variable `c`, which is a pointer or reference to an array `[1, 2]`. Now both variables `c` and `d` are referencing the same array `[1, 2]`. On line 3 we reassign variable `c` with a pointer or reference to a new array `[3, 4]`. Now variable `c` references the array `[3, 4]` and variable `d` references the array `[1, 2]`.
    - In the above example variable `c` may end up at the address 0 x 1234 in the computers memory. The memory at that address get set to a pointer or reference to the array `[1, 2]`. Variable `d` may end up at the address 0 x 1248 in the computers memory. The memory at that address is set to the value of variable `c` which is a pointer or reference to the array `[1, 2]`. Afterwards the variable `c` is reassigned a pointer or reference to a new array `[3, 4]`.
    
    ```jsx
    1 let e = [1, 2];
    2 let f = e;
    3 e.push(3, 4);
    4 e
    5 [1, 2, 3, 4]
    ```
    
    - Explain the code above? Explain what that looks like in the computer? Give Examples ?
        - On line 1 we declare a variable `e` and initialize it with the array `[1, 2]` . On line 2 we declare another variable and initialize it with the value contained by the variable `e`. On line 3 we invoke `push()` using the variable `e`.
        - Every time JavaScript program creates a new variable it causes JavaScript to allocate a spot in the memory for the value. Because arrays are objects and JavaScript doesn’t store the value of the objects in the same place. Instead it allocates additional memory for the value of the array and places a pointer or reference to the array in the space allocated for the variable.
        - In the example above variable `e` was allocated a spot somewhere in the memory for the value when it was declared. It was initialized to the value `[1, 2]`. Because arrays are objects and JavaScript doesn’t store the value of the object in the same place as the space allocated for the variable. It instead allocates additional memory for the value of the object and stores a pointer or reference to the object in the space allocated for the variable. Then another variable is defined named `f`. It is initialized to the variable `e`. Now variable `f` contains the value stored in the memory space associated with the variable `e` , which is a pointer or reference to the array `[1, 2]`. After line 2 is executed variable `e` and `f` point to the same location in memory which contain the array `[1, 2]` . On line 3 we use the variable `e` that references the array `[1, 2]` to call a built-in method `push`. `push` method mutates its caller. So when `push` method is invoked it appends the arguments `3` and `4` passed to it, into the array referenced by the variable `e`. If we try to access variable `f` it would return the mutated array, because variable `e` and `f` point to the same location in memory.