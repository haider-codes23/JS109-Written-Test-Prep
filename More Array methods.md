# More Array methods

- How does the array method `some` works?
    - `some` looks at the truthiness of the callback’s return value to determine it’s own return value. If the callback returns a truthy value for any element in the collection, then the `some` method will return `true`.
    - The method ask “if there are some values in the array for which the given callback returns a truthy value?”.
- How does the array method `every` works?
    - `every` looks at the truthiness of the callback’s return value, and if the callback returns a truthy value on every iteration only then `every` method returns `true`.
- How does the array method `find` works?
    - It takes a callback function as an argument and returns the first element for which the callback returns a truthy value. Once it finds an element for which the callback returned a truthy value it stops looking.If the callback doesn’t return a truthy value for any of the elements, `find` returns `undefined`.
- How does the array method `findIndex` works?
    - It takes a callback function as an argument and returns the index of the first element for which the callback returns a truthy value. Once it find an element for which the callback returns a truthy value it stops looking. If the callback doesn’t returns a truthy value for any of the elements, `findIndex` returns `-1`.
- How does the array method `reverse` works?
    - It reverses the elements of the array it’s called on. The first element becomes the last and the last element becomes the first. It mutates the calling array. If you don’t want the calling array to be mutated you can use the `slice` method to make a shallow copy of the array and then use `reverse` method on that shallow copy of the array.
- How does the array method `include` works?
    - `include` method returns a boolean value indicating whether the argument provided to it exists as an element within the array that invoked the method. And it uses the `===` strict equality operator. So if the array contain an object, and we check for its existence in the array using same key-value pair e.g. `let arr = ['a', 'b', {c: 'foo'}];` `arr.includes({c: 'foo'});`, it’ll return `false` because they not the same object, they occupy different locations in memory.