# Working with strings/String methods

- How to join two string?
    - We can use the `+` operator
    - Or we can use the `concat` method. It takes a string as an argument and concatenates it with the string that called the `concat` method. It doesn’t mutate its caller and returns a new string. Any operation on primitive values including `concat` method cant mutate the calling string’s value.
- How can we know if a string contains a some character or list of character/substring?
    - We can use the `include` method. It takes a string as an argument and returns a boolean value indicating whether the string argument exists within the string that called `include` method. It takes an optional second argument that specifies the index in the string at which to start looking for the substring.
- How to convert a string into an array?
    - We can use the `split` method. The basic case where we don’t provide any arguments returns an array that contains the string as its only element. The case where we provide an empty string as an argument returns an array that contains each character in the string as an individual sting element. And If you provide it any other string argument, it will be used as a separator by which to split the strings.
    
    ```jsx
    > 'One potato, two potato, three potato, four'.split(', ')
    [ 'One potato', 'two potato', 'three potato', 'four' ]
    ```
    
- How to remove white spaces from both ends of string or just from the start or just from the end?
    - We can use the `trim` method. It removes any number of whitespace characters like `\n` and `\t` from both end s of the string.
    - To remove whitespaces from the start we can use `trimstart` method.
    - To remove whitespaces from the end we can use `trimEnd` method.
- What does the string method `charAt` do?
    - It takes an index number as an argument and return the character at that specified index of the string that invoked the `charAt` method.