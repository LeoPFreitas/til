# Defining methods

## The base syntax of methods

In general case, a method has the following six components:

1. **a set of modifiers** (`public`, `static`, etc);
2. a type of the return value;
3. **a name;**
4. a list of parameters (as well known as formal parameters) in parenthesis `()`;
5. a list of exceptions;
6. **a body** containing statements to perform the operation.

## **Signatures**

The combination of the name of a method and its parameters is called the **signature**. It doesn't include the returning type, modifiers, and names of parameters.

The considered method `sum` has the following signature `sum(int, int)`.

Here are some examples of other signatures:

- `sum(double, double)`
- `min(long, long, long)`
- `getValue()`

## Naming methods

- identifiers are case-sensitive;
- an identifier can include Unicode letters, digits, and two special characters (`$`,`_`);
- an identifier can't start with a digit;
- identifiers must not be a keyword.

By the convention, method names should be a verb in lowercase or a multi-word name that begins with a verb in lowercase, followed by adjectives, nouns, etc. In multi-word names, the first letter of the second and the following words should be capitalized. Here are some correct examples:
