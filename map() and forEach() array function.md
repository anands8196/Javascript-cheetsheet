# Javascript-cheetsheet
## Array methods: Array.prototype.map() and Array.prototype.forEach().
### what’s the difference  Between Map & ForEach 

#### Definition

    forEach() — executes a provided function once for each array element.
    map() — creates a new array with the results of calling a provided function on every element in the calling array.

Code
------

The forEach() method doesn’t actually return anything (undefined). It simply calls a provided function on each element in your array. This callback is allowed to mutate the calling array.

The map() method will also call a provided function on every element in the array. The difference is that map() utilizes return values and actually returns a new Array of the same size.
Code Examples

Consider the below array. If we wanted to double each element in the array, we could use either map or forEach.

    let arr = [1, 2, 3, 4, 5]; 

ForEach:

Note that you would never return from a forEach function as the return values are simply discarded:

    arr.forEach((num, index) => {
        return arr[index] = num * 2;
    });

  Result:

    // arr = [2, 4, 6, 8, 10]

Map:

    let doubled = arr.map(num => {
        return num * 2;
    });

  Result:

    // doubled = [2, 4, 6, 8, 10]

#### Speed Considerations
'jsPerf' is a great website for testing the speed of different JavasScript methods and functions.
HforEach() was more than 70% slower than map(). 
It’s important to also understand that using map() may be preferable if you favor functional programming.

This is because forEach() affects and changes our original Array, whereas map() returns an entirely new Array — thus leaving the original array unchanged.

Which is better?
-----------------
forEach() may be preferable when you’re not trying to change the data in your array, but instead want to just do something with it — like saving it to a database or logging it out:

    let arr = ['a', 'b', 'c', 'd'];

    arr.forEach((letter) => {
        console.log(letter);
    });
    
Result

     a
     b
     c
     d

And map() might be preferable when changing or altering data. Not only is it faster but it returns a new Array. This means we can do cool things like chaining on other methods ( map(), filter(), reduce(), etc.)

    let arr = [1, 2, 3, 4, 5];
    let arr2 = arr.map(num => num * 2).filter(num => num > 5);
    
Result:

    arr2 = [6, 8, 10] 

What we’re doing above is first mapping over arr and multiplying every element in the array times 2. After this, we filter through the array and only save the elements that are greater than 5. This leaves us with a final arr2 of [6,8,10].

    Just about anything you can do with forEach() you can do with map(), and vise versa.
    map() allocates memory and stores return values. forEach() throws away return values and always returns undefined.
    forEach() will allow a callback function to mutate the current array. map() will instead return a new array.
