# Algorithms

## Complexity

- Big O notation to classifies algorithms according to how their running time or space (e.g. in memory or on disk).
- It does not depend on implementation details such as programming language, the operating system, the hardware, or programmer skills, and other implementation details.

### Big O - O(T(n))

- **T(n)** is a time complexity function that describes how the running time grows as the input size grows;
- The symbol **O** means that, when the input is large enough, the running time grows at most proportionally to the function inside parentheses.
- it describes the upper bound of the growth rate of a function and could be thought of the worst-case **scenario**;
- it describes especially well the situation for large inputs of an algorithm, but it does not care about how well your algorithm performs with inputs of small size.

### Common growth rates

- Constant time: O(1)
- Logarithmic time: O(log n)
- Square-root time: O(sqrt(n))
- Linear time: O(n)
- Log-linear time O(n log n)
- Quadratic time: O($n^2$)
- Exponential time: O($2^n$)