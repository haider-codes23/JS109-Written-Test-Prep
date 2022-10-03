# Collection Basics

- How to reference  specific characters in a string?
    - Strings use an integer-based index that represents each character in the string. The index starts from `0` and increments for each subsequent character. You can reference an element by placing this index between a pair of square brackets after the name of the variable which stores the value of the string `str[2]`
    - How to reference multiple characters within a string?
        - We can use the `String.protoype.slice` method. It takes two arguments. The first argument is the start index at which to begin extraction and the second is the end index at which to end extraction. The character at the end index isn’t included in the extracted characters.If we omit the second argument it returns all the characters beginning from the start index till the end. And if we don’t pass it any arguments it returns a copy of original string.
        
         
        
        - What happens if you provide `slice` negative arguments?
            - When given negative indices, `slice` treats them as `length + index` e.g. if the the length of string is 5 then `-4` index will be equal to index              `5 + (-4)`  which is equal to `1`.
- How to reference elements in an array?
    - Arrays are ordered list of elements, each element has a unique index number which gives its position in the array. Array indexes start from `0` and increments for each subsequent element. You can reference an element by placing the index number between a pair of brackets after the name of the variable that references the array `arr[3]`
    - How to reference multiple elements in an array?
        - We can use the `Array.prototype.slice` to extract multiple elements from an array. `slice` method returns a new array, it doesn’t mutate it’s caller. It takes two arguments. The first one is the start index at which to begin extraction and the second is the end index at which to end the extraction. End index is not included in the elements that are extracted and the array that’s returned. If we omit the second argument it returns an array that contain all the elements from the calling array beginning from the start index till the end of the array. If we omit both arguments, it returns a copy of the array.
- How to reference elements in an object?
    - Objects are a collection of key-value pairs. Each item in the collection has a name that we call the key and an associated value. The key is a string and the value could be of any data-type.Object keys are also called **properties.**
    - What happens if we initialize an object with key-value pairs that have the same name?
        - When initializing an object, the names of the key must be unique, otherwise the key-value pair get overwritten by any subsequent key-value pair with same key name.
- What happens if we try to access an index in a string or an array that is greater than the greatest used index/ out of bound index and an index less than `0` e.g a negative index?
    - Referencing an out-of-bound index or a negative index returns `undefined`.
- What happens if we try to access a property that doesn’t exist on an object?
    - It returns `undefined.`
    - Sometimes an object contains a property with `undefined` value on purpose, in that case how would we differentiate between a non-existent property and a property that has `undefined` as it’s value?
        - We can use `Object.prototype.hasOwnProperty` method which returns a boolean value indicating whether the given string exists as a property in the object.
- How to convert a string into an array?
    - We can use the `String.prototype.split` method, when called without an argument it returns an array that contains the string as its only element. However if you provide it an empty string, it returns an array that contains all the characters of the string as individual string elements. Any other string provided to `split` as an argument will be used to separate the string using the argument as the delimiter.  e.g `'apple,orange,mango'.split(','); ['apple', 'orange', 'mango']`.
- How to convert an array to a string?
    - We can use `Array.protoype.join` it returns a string with the elements of the array joined together into a string separated by commas. If we pass an empty string as argument to the `join` it joins the elements together without delimiting each character with a comma.
-