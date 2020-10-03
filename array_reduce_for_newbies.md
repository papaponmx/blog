# Array.reduce() for newbies

---
title: Array.reduce() for newbies
published: false
description: A beginner friendly explanation on how to use  Array.reduce() that you actually understand.
tags: #javascript #webdev #codenewbie
---



In this article will start by getting familiar with some key terms that will make the `Array.reduce` easier to understand.

### Prerequisites.
In order to get the most out of this post, it is important for you to be familiar with:

- Using functions with parameters.
- Callback functions.
- How return works.
- JavaScript Data types.
- Other Array methods like `Array.filter` or `Array.sort`.

--- 

Let's start with a first principles approach and go to the dictionary. According to Dictionary.com, to reduce means:

> 1. To bring down to a smaller extent, size, amount, number, etc.
> 2. To lower in degree, intensity, etc.:

**Synonyms for reduce**
diminish, decrease, shorten, abridge, curtail, contract, retrench.

With this in mind, it now easier to understand what a reducer function is. Simply put, a **reducer function reduces *n* input items to a single return value**.

Here is an example of a simple function returning the highest number in an array:

```
const numbers = [3, 4, 10, 1, 4, 3];

const reducerFunction = (numbersArray) => {
    let highestNumber;
    
  for (const singleNumber of number) {
    if (!highestNumber || highestNumber < singleNumber) {
        highestNumber = singleNumber;
    }
  }
  return highestNumber;
}

console.log('Hihest number is ', number);
```


---

Now that we know what a reducer function is, let us explore how `Array.reduce` works.

> `Array.reduce` is a method that executes a *reducer function* on each element of the array, resulting in single output value.


<!--

Key terms

✅ Reducer
Parameters
Accumulator (acc)
Current Value (cur)
Current Index (idx)
Source Array (src) 

-->

## Examples of Array.reduce in JavaScript:

## Get total of a list using Array.reduce
Imagine we are at a

## Finding an Average with the Array.reduce

