# Inside the JavaScript Engine

# **Introduction**

Learn JavaScript engines is to learn about what goes on when you run your code. That kind of knowledge helps programmers to write better, faster and smarter code.

JavaScript engines are just programs that convert JavaScript code into lower level code, so the computer can understand. This engines are embedded in browsers and web servers (Node.js) to allow run-time compilation and execution of code.

# **JavaScript isn’t is an interpreted language?**

The short answer is it depends on the implementation. JavaScript is usually categorized as interpreted although it is technically compiled. Modern JavaScript compilers actually perform Just-in-time Compilation which occurs during run-time.

# **The Engine**

There are many engines in the market and you can write our one if you want. Each engine has some kind of pipeline with an interpreter and an optimizer compiler pipeline. The interpreter generates bytecode and the optimizer generates highly optimized machine code. In these article I will use the V8 engine as example.

> V8 is Google’s open source high-performance JavaScript and WebAssembly engine, written in C++. It is used in Chrome and in Node.js, among others. It implements ECMAScript and WebAssembly, see v8.dev

# **Inside the Engine**

Whenever a programmer sends JavaScript code to the V8 engine, it follows some steps in order to display your “console.log”.

![https://miro.medium.com/max/1255/1*tjQOZYXUP4U6WuPrdUfMfg.png](https://miro.medium.com/max/1255/1*tjQOZYXUP4U6WuPrdUfMfg.png)

**Parse**

The engine makes what we call a Lexical Analysis. We give a JavaScript file to the engine and it first does a lexical analysis. This breaks the code into something called tokens to identify their meaning. After that, we know what the code is trying to do.

**Abstract Syntax Tree (AST)**

Tokens are formed into what we call AST. A syntax tree is a tree representation of the syntactic \*\*\*\*structure of the JavaScript code and we can use [this](https://astexplorer.net/) tool to analyse the AST code conversion.

If you are interested in reading more about AST, check [this article.](https://medium.com/@jotadeveloper/abstract-syntax-trees-on-javascript-534e33361fc7)

**Interpreter**

The interpreter read and translate the JavaScript files line by line on the fly (during the running of a computer program without interrupting the run). based on the generated AST code, the interpreter starts to produce unoptimized bytecode quickly.

Bytecode is not as low level as machine code, but it’s code that is able to be interpreted by the javascript engine in order to run code.

**Profiler**

The profiler is responsible to check our code. It also call a monitor that monitors and watches our code as it runs and makes notes on how we could optimize this code. Ex: How many times it is being run? What types are used? How we can optimize this code?

So, if the profiler founds some code that can be optimized, it pass this code to the Just-In-Time (JIT) compiler, so it can be compiled and runs faster. We will see these interpreter/compiler pipeline with more details during these text.

**Optimizing compiler**

The optimizing compiler’s job is to figure out what your input program does, and create an output program that it knows will do the same thing, just faster.

It doesn't translate the files on the fly. It works ahead of the time to create a translation of what code we’ve just written and it compiles down to usually a language that can be understood by our machines.

![https://miro.medium.com/max/846/1*-FXGuNKPxH-2X3mc8ERaPA.png](https://miro.medium.com/max/846/1*-FXGuNKPxH-2X3mc8ERaPA.png)

**Deoptimize**

The optimizing compiler makes certain assumptions based on the profiling data it has, and then produces highly-optimized machine code. But it's possible that at some point, one of the assumptions turns out to be incorrect. The optimizing compiler can deoptimizes code.

# **JavaScript’s object model**

JavaScript is a dynamic programming language which means that properties can easily be added or removed from an object after its instantiation. In order to write better code, we need to understand how JavaScript defines objects and how to engine deals with objects and properties.

![https://miro.medium.com/max/1272/1*DmgV8nvmyEyBbM76V-6Lww.png](https://miro.medium.com/max/1272/1*DmgV8nvmyEyBbM76V-6Lww.png)

- **Enumerable** → determines whether the property shows up in `for`-`in` loops
- **Value** → the value itself
- **Writable** → determines whether the property can be reassigned to
- **Configurable** → determines whether the property can be deleted

**Optimizing property access**

Accessing properties requires several instructions in dynamic languages like JavaScript, so almost every engine has some optimization on that. That optimization in V8 is called hidden classes and we can say that V8 attaches a hidden class to each single object. The purpose of the hidden classes is to optimize property access time.

Hidden classes work similarly to the fixed object layouts (classes) used in languages like Java, except they are created at runtime. The magic here is that objects can share hidden classes, so we need few resources and your code becomes faster.

![https://miro.medium.com/max/1628/1*5LHsAg3IMN4WRP1qhkWZ9g.png](https://miro.medium.com/max/1628/1*5LHsAg3IMN4WRP1qhkWZ9g.png)

The benefit becomes clear when we have multiple objects. No matter how many objects there are, as long as they have the same hidden class, we only have to store the information once!

This topic about optimization is very extensive and has a different name for it. We can find more information about that [here](https://richardartoul.github.io/jekyll/update/2015/04/26/hidden-classes.html).

# **Inline Caches (ICs)**

> The goal of inline caching is to speed up runtime method binding by remembering the results of a previous method lookup directly at the call site. Inline caching is especially useful for dynamically typed languages where most if not all method binding happens at runtime and where virtual method tables often cannot be used.

The main motivation behind hidden classes is the concept of IC. JavaScript Engines uses ICs to memorize information where to find properties on objects, so that we don’t need to repeat expensive property look-up on each property access. That’s significantly faster than looking up the property each time.

![https://miro.medium.com/max/1728/1*aVKSy7qS3UQx5GY3Cf-tgQ.png](https://miro.medium.com/max/1728/1*aVKSy7qS3UQx5GY3Cf-tgQ.png)

# **Take-aways**

- Always initialize your objects in the same way, so they don’t end up having different hidden classes
- Don’t mess with property attributes of array elements, so they can be stored and operated on efficiently.
