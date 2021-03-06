---
title: Array.reduce() for newbies
published: false
description: A beginner friendly explanation on how to use  Array.reduce() that you actually understand.
tags: #javascript #webdev #codenewbie
---

### Prerequisites.
In order to get the most out of this post, it is important for you to be familiar with:

- Using functions with parameters.
- Callback functions.
- How return works.
- JavaScript Data types.
- Other Array methods like `Array.filter` or `Array.sort`.

--- 

In this article will start by getting familiar with some key terms that will make the `Array.reduce` easier to understand, those key terms are: 

* Reducer.
* Accumulator.


Let's start with a first principles approach and go to the dictionary. According to Dictionary.com, to reduce means:

> 1. To bring down to a smaller extent, size, amount, number, etc.
> 2. To lower in degree, intensity, etc.

> **Synonyms for reduce**
> diminish, decrease, shorten, abridge, curtail, contract, retrench.

With this in mind, it now easier to understand what a reducer function is. Simply put, a **reducer function reduces *n* input items to a single return value**.

One of the features that makes `Array.reduce` so powerful, is that we can use an accumulator. let us learn what an accumulator is. Going back to the dictionary, an accumulator is:

> a register used to contain the results of an arithmetical or logical operation.

In the context of our programs, this register can be a variable that is refering a boolean, an array or an object.

Now that we know what a reducer function is, let us explore how `Array.reduce` works.

---

According to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce):

> `Array.reduce` is a method that executes a *reducer function* on each element of the array, resulting in single output value.

`Array.reduce` takes in two parameters:

1. A reducer function.
2. An initial value for the accumulator.

Let's dive deeper into the reducer function parameter.

### Reducer function

As we have learned before:

> A **reducer function reduces *n* input items to a single return value**.


The reducer function we provide to `Array.reduce` is executed on each element of the array. This function takes in four parameters:

1. accumulator. This is the total value of the accumulator.
2. currentItem. Current item of the array.
3. currentIndex. Current index of the array.
4. sourceArray. This is the array that we want to reduce.

Now that we have the basic concepts. Let's walk trought a few examples.


## Examples of `Array.reduce` in JavaScript:


### Get the highest number in an array using `Array.reduce`


In this example, we will: Use `Array.reduce` and define our own **reducer** function with an **accumulator** in order to get the highest number in an array:

```javascript

/**
 * Let's break it down step by step:
 
 * 1. Define an array of numbers.
 * 2. We declare the reducer function that will be applied to each element of the array.
 * 3. Within the reducer function, if the currentItem is greater than the accumulator, we will return the currentItem.
 * 4. We invoke numbers.reduce() passing our reducer function as a first parameter and 0 as an initial value for our accumulator. * 5. We store the value returned by numbers.reduce() in a variable called average.
 */


const numbers = [3, 4, 10, 1, 4, 3]; // 1. 

const reducerFunction = (accumulator, currentItem, currentIndex, sourceArray) => { // 2. 
    if (accumulator < currentItem) {
        return currentItem; // 3.
    }
    return accumulator; // 🤓 Notice that the value that we return in the reducer function, will be the value of the accumulator the next time the reducer function is invoked.
}


const highestNumber = numbers.reduce(reducerFunction, 0); // 4 and 5. Notice that 0 is the initial value for our accumulator.

console.log('Highest number is ', highestNumber); // 10
```


### Finding an Average with the Array.reduce

Imagine you have an array of products coming from the back end. In this example we will get the average price of a product in an array.

```javascript


/**
 * One more time, let's break it down step by step:
 
 * 1. Define an array of products.
 * 2. We declare the reducer function that will be applied to each element of the array.
 * 3. Within the reducer function, we summ the price of each product to the total.
 * 4. When we reached the last item in the array, we devide it by the number of elements in the array..
 * 5. We invoke products.reduce() passing our reducer function as a first parameter and 0 as an initial value for our accumulator which now is called total. 
 * 6. We store the value returned by products.reduce() in a variable called average.
 
 */
const products = [ // 1.
  {
    name: "apple",
    price: 29.76, 
  },
  {
    name: "pineapple",
    price: 41.85,
  },
  {
    name: "melon",
    price: 46.5
  }
];

const reducerFunction = (total, product, index, array) => { // 2.
  total += product.price; // 3.
  if( index === array.length - 1) { // 4.
    return total / array.length;
  } else { 
    return total; 
  }
}

const average = products.reduce(reducerFunction, 0); //5 and 6.

console.log(average) // 39.37

```


Other resources:
- [Array.protype.reduce on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce).
- [Array.reduce on W3C](https://www.w3schools.com/jsref/jsref_reduce.asp).


That's all folks. Thanks for taking the time for learning this article. 
I teach working professionals to code so they can get their first job in tech. 
If you further questions, you can ask here or [DM me on Twitter](https://twitter.com/papaponmx).
