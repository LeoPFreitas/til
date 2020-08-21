# Big Integers

- The BigInteger class is immutable which means methods of the class return new instances instead of changing existing ones.
- BigInteger operations are substantially slower than operations on built-in integer types.
- Keep in mind, that the arithmetic methods do not change instances but create a new one
- The class has a set of non-static methods to perform all standard arithmetic operations

```java
BigInteger number = new BigInteger("62957291795228763406253098")
BigInteger number = BigInteger.valueOf(1_000_000_000);

BigInteger nine = ten.subtract(BigInteger.ONE); // 10 - 1 = 9
BigInteger oneHundredTen = ten.multiply(eleven); // 10 * 11 = 110
BigInteger twelve = oneHundredTen.divide(nine); // integer division: 12
```