## C++
- `Explicitly` have to deallocate memory if memory allocated using malloc, or new keyword.

- In C++, everything is allocated on **Stack**, until unless **new** keyword is used for object or memory allocation in which case happens on **Heap**.



## Java
- **Implicit memory management**.

- **Instance methods** : In Java, we do not have separate copies for instance methods. The way this is done is by passing an implied reference to this.


## Javascript
- **Implicit memory management**.
- 


## Python
- **Implicit memory management**



## Go
+ **Implicit memory management**
+ Go manages the heap memory by garbage collection. 
+ In simple terms, it frees the memory used by orphan objects, i.e, objects that are no longer referenced from the Stack directly or indirectly(via a reference in another object) to make space for new object creation.
+ As of version 1.12, the Golang uses a non-generational concurrent tri-color mark and sweep collector


## Rust
+ Rust Lang Compiler is written in Rust.
    ```
    This is called self-hosting or bootstrapping. 
    The basic idea goes like this:

    + Write an initial compiler for a small subset of Rust using your Other   Programming Language of Choice.
    + You now have compiler C0.
    + Using the subset of Rust you have a compiler for, rewrite the source for C0 purely in Rust. Compile that program using compiler C0 to form compiler C1.
    + Add features to Rust by adding code to the compiler you just wrote to properly parse and implement those features. Compile that Rust program with C1 to form compiler C2.
    + By repeating step (3) as many times as you’d like, you can add progressively more and more features to the Rust language, with the Rust compiler always being written in Rust itself.
    ```



## Deno

