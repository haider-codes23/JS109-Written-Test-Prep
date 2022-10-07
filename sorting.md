# Sorting

- What is sorting?
    - Sorting is setting the order of items in a collection according to some criteria.
    - comparisons are at the heart of how sorting works.
    - The default behavior of `sort` does not perform numerical sorting.
- `[2, 11, 9, 4, 107, 21, 1].sort()` What would you expect the following code to return?
    - We’d expect it to return the array `[1, 2, 4, 9, 11, 21, 107]` since that’s the natural order of number, but it returns `[1, 107, 11, 2, 21, 4, 9]`. What happens here is that JavaScript coerces all the numbers in the array to strings and compares them by their unicode character code, thus all the numbers that begin with `1`move to the beginning of the array, then all the numbers that begin with `2` come next and so on. The numbers are compared digit by digit so `1` comes before `107` which comes before `11`,which comes before `2`.
- `[null, 'a', true, 1].sort()` What would you expect the following code to return?t
    - When sort is called without arguments, it coerces all the array elements to strings except those that are `undefined`, then sorts them using string comparison. `undefined` values are always placed at the end of the array. So the above code returns `[1, 'a', null, true]`
- `[undefined, 11, 'z', 'x', 'y', undefined].sort()` What does the following code return?
    - It returns `[11,'x','y','z', undefined, undefined]`
- `['c', 'a', 'e', 'b', 'd'].sort()` What does the following code return?
    - Calling sort on an array of characters returns an array of characters ordered alphabetically. So it returns the array  **`[ 'a', 'b', 'c', 'd', 'e' ]`**
- `['arc', 'bat', 'cape', 'ants', 'cap'].sort()`What does the following code return?
    - `['ants', 'arc', bat' , 'cap', 'cape']`.When working with string that have multiple characters, `sort` compares them character by character, so the strings beginning with `a` come before those beginning with `b`. if both characters are same, then the next character in each string is compared and so on. If one string is shorter than another, but equal through the length of the shorter string, then the shorter string comes before the longer one. For instance `'cap'` is shorter than `'cape'`, so `'cap'` comes before `'cape'`
- How do the operators like `<`, `>` and `===` work with strings?
    - The string order is determined by a character’s code point in the UTF-16 character encoding.
    - `'+' < '3'` What does the following expression return?
        - It returns `true`. The code point for `'+'` character in the UTF-16 character encoding is `43` and code point for character `'3'` in the UTF-16 character encoding is `51`, since `43 < 51` it returns `true`.
        - How can we find the code point of a character?
            - To find the code point of a character we can use the string method `String.prototype.charCodeAt()`.

- How can we sort an array of numbers numerically?
    - The default behavior of `sort` doesn’t perform numerical sorting since it coerces all numbers to strings before comparing them. The answer lies in the fact that sort takes an optional callback function as an argument. The return value of that callback determines the final sequence produced by sort. The `sort` method iterates over the array and supplies our callback function with two elements each time. And it arranges the relative position of elements in the array using some rules
    1. If the callback returns a value less than `0`, place `a` before `b`.
    2. If the callback returns a value greater than `0`, place `b` before `a`.
    3. If the callback returns `0`, leave the relative positions of `a` and `b` unchanged. 
    4. The result is an array of numbers sorted in ascending order. 
    
    ```jsx
    [2, 11, 9, 4, 107, 21, 1].sort((a, b) =>{
    	if (a < b) {
    		return -1;
    	} else if (a > b) {
    		return 1;
    	} else if {
    		return 0;
    	}
    
    }); // => [1, 2, 4, 9, 11, 21, 107]
    
    // We can simplify our callback function a bit.
    // We know that we want to return a negative number
    // when a is less than b and positive number when a is greater than b
    // instead of the if/else logic we can just use 
    // return a - b
    
    [2, 11, 9, 4, 107, 21, 1].sort((a,b) => a- b);
    // sort doesn't compare every single pair of value 
    ```
    
    - If you want to sort an array of numbers in descending order all we have to do is flip the logic of our callback so that when `a` is less than `b` it returns a positive number so that sort places `b` before `a`, when `a` is greater than `b` it returns a negative number so that sort places `a` before `b`  and when `a` is equal to `b` it should return 0 so that sort doesn’t change the relative positions of `a` and `b`
    
    ```jsx
    [2, 11, 9, 4, 107, 21, 1].sort((a, b) => b - a);
    ```
    

```jsx
let words = ['go', 'ahead', 'and', 'jump'];
```

- How would you sort the following array by length of each word?
    - `words.sort((a, b) => a.length - b.length)`