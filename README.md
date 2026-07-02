# Rust Borrow Checker Kata

This repository is a hands-on, self-guided learning module designed to build a robust mental model of the Rust borrow checker. It is not a library, but a set of exercises to be completed locally. The goal is to make you productive in Rust by mastering its most unique feature: the ownership and borrow system.

This module is structured as a series of "Katas" (exercises). You will fix broken code by editing files and running `cargo check`. This interactive process helps solidify the concepts by letting you experience the compiler's errors firsthand and then fix them.

## Learning Philosophy

The pedagogical approach is designed to address common pitfalls for Rust newcomers:

1.  **Compiler Errors are the Teacher:** You will learn by doing. Each exercise presents you with non-compiling code. Your task is to read the code, understand the goal, run the compiler, interpret the error, and apply the fix described in the comments.
2.  **The Escape Hatch vs. The Idiomatic Fix:** We explicitly teach the difference between a quick workaround (`.clone()`) and the idiomatic, efficient solution (borrowing). This prevents the anti-pattern of "appeasing the compiler" with expensive copies and instead teaches the underlying principles of memory management in Rust.
3.  **Progressive Scaffolding:** Concepts are introduced one at a time, building from simple ownership rules to more complex scenarios involving functions and structs. Lifetimes, a more advanced topic, are intentionally saved for last.

## Architecture

The learning path is a strict, progressive order of exercises. Each lesson is a separate binary within a Cargo workspace.

```mermaid
graph TD
    A[Start: Clone Repo] --> B{Lesson 1: Ownership & Moves};
    B --> C{Lesson 2: Immutable Borrows};
    C --> D{Lesson 3: Mutable Borrows};
    D --> E{"Lesson 4: The Core Lesson"};
    E --> E_A[4a: Fix with .clone()];
    E --> E_B[4b: Refactor to use Borrows];
    E_A & E_B --> F{Lesson 5: Scaling Patterns};
    F --> F_A[5a: Functions];
    F --> F_B[5b: Structs];
    F_A & F_B --> G{Lesson 6: Demystifying Lifetimes};
    G --> H[End: Mastery];

    style A fill:#cfc,stroke:#333,stroke-width:2px
    style H fill:#cfc,stroke:#333,stroke-width:2px
    style E fill:#f9f,stroke:#333,stroke-width:2px
```

## Concepts Covered

-   Value Ownership and Moves
-   Immutable Borrows (`&T`)
-   Mutable Borrows (`&mut T`)
-   The "Many Readers, Zero Writers" Rule
-   The "One Writer, Zero Readers" Rule
-   Contrasting `clone()` vs. Borrowing
-   Function Signatures and Ownership (`String` vs. `&str`)
-   Method Signatures and Structs (`&self` vs. `&mut self`)
-   Lifetime Annotations (`<'a>`)

## How to Run the Exercises

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/aastom/rust-borrow-checker-kata.git
    cd rust-borrow-checker-kata
    ```

2.  **Start with the first lesson:** Open `src/bin/01-ownership-move.rs` in your editor.

3.  **Run the compiler:** In your terminal, run `cargo check` for that specific lesson to see the error.
    ```bash
    cargo check --bin 01-ownership-move
    ```

4.  **Read and Fix:** Read the comments in the file to understand the concept and the error. Follow the `// TODO:` instruction to fix the code.

5.  **Verify your fix:** Run `cargo check` again. If it compiles without errors or warnings, you've succeeded!

6.  **Move to the next lesson.**

## References

-   [The Rust Book: What is Ownership?](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)
-   [Rust By Example: Borrowing](https://doc.rust-lang.org/rust-by-example/scope/borrow.html)
-   [Rustonomicon: Lifetimes](https://doc.rust-lang.org/nomicon/lifetimes.html)
