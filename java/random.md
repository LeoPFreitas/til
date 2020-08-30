# Random

The class `Random` can generate random values of different types, such as `int`, `long`, `double`, and even `boolean`. We will consider how to use this class for numbers.

```java
Random random = new Random();

Random random = new Random(100000);
```

## Methods

After we've created a generator, we can invoke one of the following methods of it:

- `int nextInt()` returns a pseudorandom value of the `int` type;
- `int nextInt(int n)` returns a pseudorandom value of `int` type in the range of from `0` (inclusive) to `n
` (exclusive);
- `long nextLong()` returns a pseudorandom value of `long` type;
- `double nextDouble()` returns a pseudorandom value of `double` type between `0.0` and `1.0`;
- `void nextBytes(byte[] bytes)` generates random bytes and places them into a user-supplied byte array.

### Pseudorandom integers from range

```java
int next = random.nextInt(upper - lower + 1) + lower;
```