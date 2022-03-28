# Big O Notation

Is the language and metric we use to describe the efficiency of algorithms.
The concept basically gives you one way of describing how the time that takes to run your functions grows as the size of the input grows.
Knowledge of Big O notation gives the ability to write better code, readable and scalable.

## Big O, Big Theta and Big Omega

An algorithm execution have 3 different scenarios:

- Best case
- Average case
- Worst case

- Big O: It's a complexity that is going to be less or equal to the worst case
- Big Omega: It's a complexity that is going to be at least more than the best case
- Big Theta: It's a complexity that is within bounds of the worst and the best case

## Time complexity examples

- O(1) - Constant Time
  Example:

```js
// Access a element by index in array
array = [1, 3, 4, 5, 6, 7, 8];
array[0]; // It takes constant time to access the element doesn't matter how elements
```

- O(N) - Linear
  Example:

```js
// Looping through array elements
array = [1, 3, 4, 5, 6, 7, 8];
for (const n of array) {
  console.log(n);
}
// Linear time, when input increases, time increases.
```

- O(LogN) - Linear
  Example:

```python
# Find an element in sorted array
array = [1, 3, 4, 5, 6, 7, 8]
for index in range(0, len(array), 3):
  print(array[index])
# Logarithmic time since it is visiting only some elements
```

- O(N^2) - Quadratic time
  Example:

```js
// Loop through an matrix
array = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

for (const x of array) {
  for (const y of x) {
    console.log(y);
  }
}
```

- O(2^n) - Exponential time
  Example:

```python
# Double recursion in Fibonacci
def fibonacci(n):
  if n <= 1 :
    return n
  return fibonacci(n-1) + fibonacci(n-2)
```

## Space complexity examples

Space complexity is a measure of the amount of working storage an algorithm needs.

## Drop constants and the non dominant terms

This means that we can easily eliminate some values from asymptotic analysis.
This means that O(2n) can be drop to O(n), O(n^2+n) to O(n^2)

- Why do we drop constants and non dominant terms?
  - Its very possible that O(n) code is faster than O(1) code for specific inputs
  - Different computers with different architectures have different constant factors
  - Different algorithms with the same basic idea and computational complexity might have slightly different constants.

## Add vs Multiply

If your algorithm is in the form "do this then, then when you are all done do that" then you add the run times
But if your algorithm is in the form "do this for each time you do that" then you multiply the run times

## How to measure the codes using Big O

- Rule 1
  - Any assignment statements and if statement that are executed once regardless of the size of the problem. O(1)
- Rule 2
  - A simple for loop form 0 to n (with no internal loops). O(n)
- Rule 3
  - A nested loop of the same type takes quadratic time complexity. O(n^2)
- Rule 4
  - A loop, in which the controlling parameter is divided by two at each step. O(log n)
- Rule 5
  - When dealing with multiple statements, just add them up

## How to measure Recursive Algorithms?

We assume that if a function calls itself recursively, it takes a M(n) time complexity.
And inside this function, if condition will take constant time complexity and the returning of first element will take also constant time operation.

## Questions

1. What is the runtime of the below code?

```python
def foo(array):
  sum = 0 # O(1)
  product = 1 # O(1)
  for i in array: # O(n)
    sum += i # O(1)
  for i in array: # O(n)
    product *= i # O(1)
  for i in array: # O(n)
    product *= i # O(1)

  print("Sum = "+str(sum)", Product = ",+str(product))
```

**Answer: O(n)**

2. What is the runtime of the below code?

```python
def printPairs(array):
  for i in array: # O(n^2)
    for j in array: # O(n)
      print(str(i) + ","+str(j)) # O(1)
```

**Answer: O(n^2)**

3.  What is the runtime of the below code?

```python
def UnorderedPairs(array):
  for i in range(0, len(array)):
    for j in range(i+1, len(array)):
      print(array[i] + "," + array[j])
```

**Answer: O(n^2)**

4.  What is the runtime of the below code?

```python
def printUnorderedPairs(arrayA, arrayB):
  for i in range(len(arrayA)):
    for j in range(arrayB):
      if(arrayA[i] < arrayB[j]):
        print(str(arrayA[i]) + "," + str(arrayB[i]))
```

**Answer: O(n)**
