# Sorting problem

It is possible to sort data of different types:

- numbers in accordance with the arithmetic order;
- unicode characters in accordance with their order in the Unicode character table;
- strings in accordance with the lexicographical order or their sizes;
- dates and time in accordance with the chronology order.

### Key features of sorting algorithms

- **Time efficiency.** The size of an array to sort is very important for efficiency. If we want to sort an array consisting of a few dozen elements, we can use any sorting algorithm. But what if the array contains a lot of data? In that case, we should use only the effective sorting algorithms, otherwise, the results might take too long.
- **Stability.** An array to sort may contain several identical elements. Stable sort algorithms always sort identical elements in the same order as they appear in the input. Otherwise, the sorting algorithm is unstable. The stability is important when we sort complex structures such as objects, tuples or something else.
- **In-place/out-of-place sorting.** An algorithm performs an **in-place** sorting if it requires only a constant amount of additional space, otherwise, the algorithm performs an **out-of-place** sorting. The larger the size of the array, the more additional memory is required by the **out-of-place** algorithms.
- **Internal or external sorting**. An algorithm performs an **internal** sorting if sorting data are kept entirely within the main memory of the computer. **External** sorting is required when the data do not fit into the main memory of the computing device and instead, they must be kept in the slower external memory (usually a hard drive).