# The entire flow of a JS source program

1. Development --> transpile (babel) --> packed (webpack) --> delivery to JS engine
2. JS engine parses the code to an Abstract Syntax Tree (AST)
3. Engine converts that AST to a binary intermediate (IR), then the JIT compiler refine/convert
4. JS VM executes the program

Complete explanation [here](https://github.com/LeoPFreitas/You-Dont-Know-JS-1/blob/2nd-ed/get-started/ch1.md)

## AST

AST is an acronym for Abstract Syntax Tree. It is a representation of tokens generated from statements and expressions in a programming language. With the AST, the interpreter or the compiler can generate machine code or evaluate an instruction. 

Complete explanation [here](https://blog.bitsrc.io/what-is-an-abstract-syntax-tree-7502b71bde27)
