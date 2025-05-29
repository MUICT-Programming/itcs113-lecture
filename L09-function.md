# Fundamentals of Programming - Lecture 9

## Today's Topics

* What is a function?
* Defining a function
* Function prototype
* Function parameters
* Formal and actual parameters
* Function call: pass by value
* Built-in functions

---

## What is a Function?

A **function** is a self-contained block of code that performs a specific task.

### Real-life Analogy

Imagine a sequence of tasks:

```c
// Husband's task for taking out the trash
walk_to_trash_bin();
tie_bag();
pickup_bag();
walk_outdoor();
put_down_bag();
wash_hand();

// Wife's version
find_husband();
take_out_trash();
```

These sequences are like functions—each performs a defined set of actions.

### Built-in Functions in C

You've already used functions:

```c
#include<stdio.h>

int main() {
    int a;
    scanf("%d", &a);
    printf("Oh, Hello Function!\n");
    printf("You input number: %d\n", a);
    return 0;
}
```

Functions such as `scanf` and `printf` are built-in to the C standard library.

### Why Use Functions?

* Break complex tasks into manageable sub-tasks
* Improve code **readability** and **reusability**
* Easier to **test and debug**
* Keep variable scope limited and avoid name clashes

---

## How to Design a Good Function

A well-designed function should:

* Perform **one** specific task
* Be **reusable**
* Accept **input arguments**
* Return **output values**

There is no single correct design—the best structure depends on the problem you're solving.

---

## Example: Without Functions

```c
int main() {
    int result1 = 5 + 5;
    int result2 = 6 + 6;
    int result3 = 7 + 7;
    int result4 = 8 + 8;
    int result5 = 9 + 9;

    printf("The result is %d\n", result1);
    printf("The result is %d\n", result2);
    printf("The result is %d\n", result3);
    printf("The result is %d\n", result4);
    printf("The result is %d\n", result5);

    return 0;
}
```

This code contains a lot of **redundancy**.

---

## Example: With a Function

```c
int add(int a, int b) {
    int sum = a + b;
    printf("The result is %d\n", sum);
    return sum;
}

int main() {
    add(5, 5);
    add(6, 6);
    add(7, 7);
    add(8, 8);
    add(9, 9);
    return 0;
}
```

If we want to change the output format, we only need to modify it **once** inside the `add()` function.

---

## How to Use Functions

We focus on **what** the function does, not **how** it does it.

### Example

```c
printf("Hello World\n"); // prints output
scanf("%d", &x); // reads input
```

---

## Types of Functions

1. **Built-in Functions**

   * Provided by C standard library
   * Require `#include <library>`
   * Example: `math.h`, `stdio.h`

2. **User-defined Functions**

   * Written by the programmer
   * Specify input, output, and the internal steps

---

## Defining a Function

### Example

```c
float get_circle_area(float r) {
    float r_square = r * r;
    float area = 3.14 * r_square;
    return area;
}
```

* Function name: `get_circle_area`
* Parameter: `float r`
* Return type: `float`

---

## Function Header Syntax

```c
return_dtype func_name(dtype1 param1, dtype2 param2) {
    // statements
    return return_value;
}
```

* `return_dtype`: type of returned value (e.g., `int`, `float`, `void`)
* `func_name`: name of the function
* Parameters specify input types and order

---

## Simple Example

```c
#include <stdio.h>

void say_hello_world() {
    printf("Hello World!\n");
}

int main() {
    say_hello_world();
    printf("===========\n");
    say_hello_world();
    return 0;
}
```

Output:

```
Hello World!
===========
Hello World!
```

---

## Function Prototype

A **function prototype** is a forward declaration.
It tells the compiler what the function will look like:

```c
int add(int x, int y);
float get_area_rectangle(float h, float w);
void say_hello_world();
```

### Example With Prototype

```c
#include <stdio.h>
float get_circle_area(float r);

int main() {
    float area1 = get_circle_area(3);
    float area2 = get_circle_area(7);
    return 0;
}

float get_circle_area(float r) {
    return 3.14 * r * r;
}
```

---

## Function Parameters

* **Formal parameters**: declared in the function definition.
* **Actual parameters**: values passed during a function call.

### Example

```c
float get_circle_area(float r);  // Prototype

float get_circle_area(float r) { // Definition
    return 3.14 * r * r;
}

int main() {
    float area = get_circle_area(4.0); // Actual parameter
    return 0;
}
```

---

## Function Call: Pass by Value

In C, function arguments are passed **by value**.
This means that copies of the actual parameters are passed to the function.

### Example

```c
float get_circle_area(float r) {
    r = 0.7; // Changes to r do not affect caller
    return 3.14 * r * r;
}
```

```c
int main() {
    float r1 = 4.2;
    float area1 = get_circle_area(r1);
    // r1 remains 4.2
    return 0;
}
```

---

## Questions for Practice

### Q1:

```c
void hello() {
    printf("hello\n");
}
int main() {
    hello();
    hello();
    return 0;
}
```

**Output:**

```
hello
hello
```

### Q2:

```c
int main() {
    hello();
    hello();
    return 0;
}
void hello() {
    printf("hello\n");
}
```

**Output:** Same as Q1 (but now definition is placed after `main`)

### Q3:

```c
int get_two_multiply_two() {
    return 2 * 2;
}
```

Use return value in `main` as:

```c
int result = get_two_multiply_two();
```

### Q4: Function Prototypes

* `int get_sum(int x, int y);`
* `void print_hello();`
* `int get_two_plus_two();`
* `float get_circle_area(float r);`

---

## C Standard Library Functions

To use standard functions, include headers such as:

```c
#include <math.h>
#include <stdio.h>
```

### Example: `pow` function

```c
#include <math.h>
#include <stdio.h>

int main() {
    int base, exponent;
    scanf("%d %d", &base, &exponent);
    double result = pow(base, exponent); // result is double
    return 0;
}
```

* Casting: You can cast from `int` → `float` → `double` **without loss**.
* Avoid casting from `double` → `int`, as it **loses precision**.

---

## Summary

* Functions make programs modular and reusable.
* Define input/output clearly.
* Use prototypes to inform the compiler.
* C uses **pass by value**.
* Use the C Standard Library to save effort and ensure correctness.
