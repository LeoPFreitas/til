# Multidimensional Array

Some structures such as matrices and tables are conveniently modeled by two-dimensional arrays. To create a multi-dimensional array we could use an array as an element of another array.

> To iterate through multidimensional arrays nested loops are often used

## 2-dimensional arrays

- In this case, the length of twoDimArray is 3 (because it includes 3 arrays as elements). The length of each nested array is 4.

```java
int[][] twoDimArray = {
        {1, 2, 3, 1}, // first array of int
        {3, 4, 1, 2}, // second array of int
        {4, 4, 1, 0}  // third array of int
};

int number = twoDimArray[0][2]; // it is 3
```

- All nested arrays can have a different length

```java
int[][] twoDimArray = new int[3][];

twoDimArray[0] = new int[] { 1, 2, 3, 4 }; // the length is 4
twoDimArray[1] = new int[] { 5, 7, 3};     // the length is 3
twoDimArray[2] = new int[] { 8 };          // the length is 1

// let's output the array
for (int i = 0; i < twoDimArray.length; i++) {
    System.out.println(Arrays.toString(twoDimArray[i]));
}

// [1, 2, 3, 4]
// [5, 7, 3]
// [8]
```

## 3-dimensional arrays

Let's fill each 2D array of the cubic by the following rules:

- the first 2D array must contain elements equal 1;
- the second 2D array must contain elements equal 2;
- the third 2D array must contain elements equal 3.

```java
int[][][] cubic = new int[3][4][5]; // an three-dimensiona array (cube)

int current = 1; // it stores a value to fill elements

for (int i = 0; i < 3; i++) { // iterating through each 2D array ("table" or "matrix")
    for (int j = 0; j < 4; j++) { // iterating through each 1D array ("vector") array of a "matrix"
        for (int k = 0; k < 5; k++) { // iterating through each element of a vector
            cubic[i][j][k] = current; // assign a value to an element
        }
    }
    current++; // get the next value to the next "matrix"
}

for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 4; j++) {
        for (int k = 0; k < 5; k++) {
            System.out.print(cubic[i][j][k] + " ");
        }
        System.out.println();
    }
    System.out.println();
}

// 1 1 1 1 1
// 1 1 1 1 1
// 1 1 1 1 1
// 1 1 1 1 1

// 2 2 2 2 2
// 2 2 2 2 2
// 2 2 2 2 2
// 2 2 2 2 2

// 3 3 3 3 3
// 3 3 3 3 3
// 3 3 3 3 3
// 3 3 3 3 3
```

- It is also possible to use for-each loops

```java
// this code fills the 3-dimensional array
int current = 1;
for (int[][] dim2Array : cubic) {     // for each 2-dim array
    for (int[] vector : dim2Array) {  // for each 1-dim array (vector) of 2-dim array
        Arrays.fill(vector, current); // fill the vector
    }
   current++; // the next current
}

// this code prints all 2-dimensional arrays
for (int[][] dim2Array : cubic) {
    for (int[] vector : dim2Array) {
        System.out.println(Arrays.toString(vector));
    }
    System.out.println();
}
```
