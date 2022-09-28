# Arrays

- What are Arrays? What syntax do we use to access an array?
    - Arrays are an ordered list of elements. Arrays are heterogeneous, has both number and string value. Arrays can include anything even arrays and objects. Each element in the array has a **unique index number** that gives its position in the array.
    - The syntax puts an index number between square brackets after the array’s name or value.
- How to modify array?
    - How to replace and add new elements in an array?
        - We can replace elements in an array using the `[]` operator. To replace an element you just have to put the index number of the element that you want to replace between the `[]` operator after the array’s name or value e.g. `animalNames[3]`. And at last you assign it a value using the `=` assignment operator. e.g. `animalName[3] = "horse"`.
        - To add a new element in an array using the `[]` operator, we need to know the index position of the next to the last element so that we can add a new element at the next to last used index position in the array, we can find it out using the array length property `.length` e.g. `animalNames.length`.
        - Another way to add a new element is by using the `push()` method. The `push()` method appends its arguments to the end of caller(the array), which mutates the caller. It returns array’s new length.
        - Another way to add a new element to an array is to use the `concat()` method. It’s similar to `push()` but it doesn’t mutate it’s caller. The `concat()` method creates a new array. The array will first be populated by the elements in the object on which the `concat()` is called. Then, for each argument, it’s value will be concatenated into the array.
        - Explain different ways how to remove element from an array?
            - We can use the `pop()` method. It is the inverse of `push()` method. While `push` adds an element to the end of the array, `pop()` removes and returns the last element of the array.
            - We can also use the `splice()` method. It changes the content of the array by **removing or replacing** existing elements and/or adding new elements. The first argument that it takes is the **start index** at which to start changing the array. The second argument is the **delete count**, an integer that indicates the number of elements to remove in the array beginning from **start index**. At last we can pass as many values(arguments) as we want, to append to the array from the starts index. It returns an array containing the deleted elements.
        - Why are variables declared with `const` and initialized to an array a little strange?
            - They are a little strange because you cannot reassign that variable another array, in other words you cannot change what array the variable points to. But the content of the array can be modified e.g. you can add/ replace an element.
            - What can we do if we want the elements of the array to be a const so that they too can’t be modified?
                - We can use the `Object.freeze()` method e.g. `const number = Object.freeze([1, 2, 3])` . Now if you tried modifying the array e.g. adding/replacing element it wouldn’t mutate the array. And its important to remember that `Object.freeze()` works only one level deep in the array.
- How does `forEach()` method iterate over an array? What’s a call back function?
    - To use `forEach()` method you need a callback function that you pass to `forEach()` as an argument. The `forEach()` method, during each iteration invokes the callback function with the element `forEach()` is currently iterating over, as an argument. In the end `forEach()` returns undefined.
    - A callback is a function that you pass to another function as an argument.
- What is `map()` method used for? Give Examples? What does `map()` method return?
    - It’s used for transforming array. It’s a built-in array method that creates a new array whose elements depend on the original content of the array. E.g. you want to create a new array that contains the squares of all the numbers in the calling array. `let squares = numbers.map(num => num * num)` (here we’re using an arrow function as a callback function).
    - `map()` method returns a new array that contain one element for each element of the calling array, with each element set to the return value of the callback.
- What is `filter()` method used for? How does it work?
    - It’s an array iteration method. It returns a new array that includes all the elements from the calling array for which the call back returns a truthy value.
    - `filter` iterates over the elements of the array. During each iteration, it invokes the callback function, using the value of the current element as an argument. If the callback function returns a truthy value, `filter` appends the element’s value to a new array. Otherwise it ignores the elements value and does nothing.When `filter` finishes iterating, it returns the array of selected elements. It doesn’t mutate the caller.
- What is `reduce()` method used for? How does it work?
    - It is used to effectively reduce the contents of the array to a single value.
    - It takes two arguments, a callback function and and a value that initializes something called the accumulator. The callback takes two arguments, the current value of the accumulator and an element from the array. The callback function returns a value that will be used as the accumulator in the next invocation of the callback.
- Which oddities do arrays in JavaScript have?
    - Array’s index always start from `0` and are non-negative numbers.
    - The `length` property of array always returns a number greater than the greatest used index position of array.
    - Array’s data type is `object`. So if you want to find out if some variable references an array then you can use `Array.isArray()` method.
    - If you change an array length property to a new smaller value, the array get truncated.
    - If you change an array length property to a new larger value, the array expands to the new size. The new elements do not get initialized. JavaScript treats the **unset elements** as missing, but the length property includes the unset elements.
    - You can create array elements with indexes that use negative number or non-integer values or even non-numerical values. But these elements are not true elements; they are properties on the array object and do not count towards the length of the array.
- What happens when we compare two arrays that contain the same elements for strict equality? Use examples to explain your answer?
    - E.g. we have two arrays `[1, 2, 3]` and `[1, 2, 3]` both contain the same elements. If we compared them for strict equality it would return `false`.  Because they are not the same arrays as they occupy different locations in memory.
    - Now if we had an array assigned to a variable and we assigned that variable to another variable, then if we compared the two variables, it would return `true`. Because both variables refer to the same location in memory. JavaScript treats two arrays as equal only when they occupy the same space in memory.
    
    ```jsx
    > [1, 2, 3] === [1, 2, 3]
    = false
    > let arr = [1, 2, 3]
    > let a = arr
    > a === arr
    > true
    ```
    
- Other Array methods
    - What does the `include` method do?
        - It determines whether an array includes an element provided to it as an argument. It returns a boolean value.
        
    - What does `slice` method do?
        - It extracts and returns a portion of the array. It takes two optional arguments. The first is the index number at which the extraction begins and the second is the index number where the extraction ends. The element at the second index is excluded. If you omit the second argument, `slice` returns the rest of the array starting with the index given by the first argument. If you don’t provide an argument at all `slice` returns a copy of the array.
- A persons character is not judges when they ride the wave of success. Your character is put to the test when your back is against the wall. And for me that time is now. Failure gives you two choice either you stay down or you get up. Well I’m up, i’m fired up, because i have figured it out. I have figured out that i need to keep standing and just plain old do something that i should have done a long time ago.