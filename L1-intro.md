# ITCS113 Fundamentals of Programming - Lecture 1

## Today’s Topics

* Intro to Programming
* Design algorithm
* Step by step in C programming
* Structure of a Basic C Programming
* Data types
* Variable and Declaration
* Basic Input & Output
* Arithmetic Operations

---

## Introduction to Programming

To operate a computer, humans need to communicate with it. Since we don't speak binary, we use **programming languages**.

### Programming Language

* A language that specifies a set of instructions to create programs.
* Examples: C, C++, Java

### Computer Program

* A collection of data and instructions to operate a computer.
* A program or set of programs is called **software**.

### Programming

* The process of writing instructions in a language that the computer and other programmers can understand.

---

## Steps in Creating a C Program

1. Analyze problems and design a solution.
2. Write instructions in C using a text editor (e.g., Visual Studio Code).
3. Compile source code using a compiler such as `gcc`.
4. If errors exist, debug the code.
5. Run the program to see the result.

---

## Designing Algorithms

### What is an Algorithm?

A procedure for solving a problem in terms of:

* The **actions** to be executed
* The **order** of these actions

### Problem-Solving Process

1. Understand the problem
2. Design an algorithm
3. Write the program
4. Debug and test

### Describing Algorithms

* **Pseudocode**: A readable plain-English version of steps
* **Flowchart**: Diagram showing stepwise instructions

#### Pseudocode Example: Average of 3 numbers

```plaintext
Input three numbers
Sum the numbers
Divide the sum by 3
Display the average
```

#### Flowchart Example:

Start → Input numbers → Add → Divide → Display → End

---

## Structure of a C Program

### Example Program

```c
#include <stdio.h>
int main() {
    printf("Hello World");
    return 0;
}
```

### Key Components

* **#include**: Includes a standard library header (e.g., `stdio.h`)
* **main()**: Entry point of the program
* **Statements**: Series of instructions in the body
* **Comments**: Used for code documentation

## Data Types

### Integer Types

* `int`, `short`, `long`, `unsigned int`, etc.
* Hold whole numbers

### Character Type

* `char`: Stores a single character (e.g., `'A'`)
* Stored using ASCII encoding

### Floating-point Types

* `float`, `double`, `long double`
* Hold real numbers with decimals

---

## Variables and Declarations

### Variable Declaration

```c
int x;
char grade = 'A';
```

* Variables must be declared before use.
* Variable names must not conflict with **keywords**.

### Valid/Invalid Names

* Valid: `sum`, `total_score`, `_value`
* Invalid: `int`, `1number`, `x+y`

---

## Assignment and Operators

### Examples

```c
x = x + 5;  // or x += 5;
sum = 3 + 4 * 2;
```

### Compound Operators

* `+=`, `-=`, `*=`, `/=`, `%=`

---

## Type Conversion

### Implicit Type Conversion

```c
int a = 5;
float b = a;
```

### Explicit Type Conversion (Casting)

```c
double x = 10.7;
int y = (int)x; // y = 10
```

---

## Basic Input and Output

### Input

```c
scanf("%d", &x);
```

### Output

```c
printf("Value: %d", x);
```

---

## Arithmetic Operations

### Operators

* `+` Addition
* `-` Subtraction
* `*` Multiplication
* `/` Division
* `%` Modulus (integers only)

### Operator Precedence

1. Unary `-`
2. `*`, `/`, `%`
3. `+`, `-`

Use `()` to control precedence.

---
