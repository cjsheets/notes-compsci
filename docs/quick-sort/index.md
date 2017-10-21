<h1>Binary Search</h1>

Asymptotic complexity is represented using Big O notation. It's a metric to describe the efficiency of algorithms.

In Order, common complexities are O(log x), O(x), O(x log x), O(x^2), O(2^x), O(x!)

## Big O, Theta, Omega

- Big O: In academia, upper bound on time.
- Big Omega: lower bound on time complexity
- Big Theta: Combination of O and Omega

## Amortized Time

Some tasks have periodic or potential slow components. Example, inserting into a fixed-size array is O(1).
However, when the array is full you have to copy every element to a new, larger array (say, 2x size). This copy
operation is O(x). Because it happens increasingly infrequently you can say the time complexity is O(X) while
amortized time is O(1).

## Log N Runtime

