# Data encapsulation

According to the data encapsulation principle, the fields of a class are hidden from being directly accessed from other classes. The fields can be accessed only through the methods of that particular class. To access hidden fields programmers write special types of methods: getters and setters.

Using these methods gives us some advantages:

- the fields of a class can be made read-only, write-only or both;
- a class can have total control over what values are stored in the fields;
- users of a class don't know how the class stores its data and don't depend on the fields.

## Getters and Setters

- **getters** start with **get**, followed by the variable name, with the first letter of the variable name capitalized;
- **setters** start with **set**, followed by the variable name, with the first letter of the variable name capitalized.
- A getter for a boolean field start with is, followed by the variable name.
