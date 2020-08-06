# Binary Search

- Fast algorithm for finding the position of an element in a **sorted array**
- $O(log(n))$

## Pseudocode

1. Let `min = 0` and `max = n-1`.
2. Compute `guess` as the average of `max` and `min`, rounded down (so that it is an integer).
3. If `array[guess]` equals `target`, then stop. You found it! Return `guess`.
4. If the guess was too low, that is, `array[guess] < target`, then set `min = guess + 1`.
5. Otherwise, the guess was too high. Set `max = guess - 1`.
6. Go back to step 2.