# Javascript-cheetsheet

Map Definition & Syntax
 ----------------------------


The map() method is used to apply a function on every element in an array. A new array is then returned.

Syntax:

     let newArr = oldArr.map((val, index, arr) => {
      // return element to new Array
     });

newArr — the new array that is returned
oldArr — the array to run the map function on
val — the current value being processed
index — the current index of the value being processed
arr — the original array

Map vs. For Loop Example
-----------------------------------

You can think of map() as a for loop, that is specifically for transforming values. Consider the following code:

        var arr = [1, 2, 3, 4];
        var plus5 = [];

        for(var i = 0; i < arr.length; i++) {
        plus5[i] = arr[i] + 5;
        }

       plus5 = [6,7,8,9]

This code results in a new array where each value is 5 more than it was in the old array. While this code works, there is a much easier way to achieve the same result — using the map() function.
To use the map() function, we’ll start with the same simple array of numbers:

let arr = [1,2,3,4];

arr is the array we’re going to map over. Since we want to add 5 to each value, all we need to do is return the value plus 5:

    let plus5 = arr.map((val, i, arr) => {
      return val + 5;
    });

Now if we log out the value of our two arrays, we can see the arr array is unchanged, and the plus5 array has our new values:

    arr = [1,2,3,4];

    plus5 = [6,7,8,9]

There is no loop needed, and we no longer have to add values manually to an array. When working with the map() function, all you need to do is define what you want to happen and return it. Map() will handle the rest.


### Map Example #2

In this example we’ll utilize both the value and index arguments. We’ll start with the same basic array as last time:

    let arr = [1,2,3,4];

This time however we’re going to return an object .This object will contain the index and the value at that index. To do this, we’ll utilize the i argument:

    let newArr = arr.map((val, i, arr) => {
      return {
        value: val,
        index: i
      };
    });


This will create an array of objects for us within our newArr:

    arr = [1,2,3,4];


      newArr = [
      {value: 1, index: 0},
      {value: 2, index: 1},
      {value: 3, index: 2},
      {value: 4, index: 3}
    ]

### Side Note

Hopefully you’re starting to see that whatever we return within our map array is what is used to create our new array. You can utilize the current value, current index, or the entire array to help determine what you want to return.
You could even do something goofy like this (although there is really no point) and just return a static string:

let arr = [1,2,3,4];

    let newArr = arr.map(() => {
      return 'cats';
    });

// newArr = ['cats', 'cats', 'cats', 'cats']

### Map Example #3

Up to this point, all of our examples have transformed all of the values in the old array. What if we only want to transform some of the values in our array? There are a number of ways we could tackle this problem, here’s one possible solution.
In this example we have a simple array:

    let arr = [1,2,3,4];

We want to double the even numbers and leave the odd numbers the same. In order to accomplish this, we can add logic within our map() function:

    let newArr = arr.map((v,i,a) => {
      return v % 2 === 0 ? v * 2 : v;
    });

// newArr = [1,4,3,8];

our even values have been doubled and our add values remain untouched.
Here it is written differently:

    let newArr = arr.map((v,i,a) => {
      if (v % 2 === 0){
        return v * 2;
      } else {
        return v;
      }
    });

// newArr = [1,4,3,8];
