# Fundamentals of Programming - Lecture 11

## Pointers in C - Part 1

### Topics Covered

* Variables and addresses
* Pointers and dereferencing
* Pass by reference
* Using pointers with arrays

---

## Variables and Addresses

### What is a Variable?

A **variable** is a symbolic name associated with a value that can change during program execution. The compiler allocates a specific block of memory for each variable, and the size depends on its data type.

### Example:

```c
int j, k;
k = 2;
j = 7;
k = j; // k now holds 7
```

Each variable has:

* **Value**: the data it holds
* **Address**: memory location where it's stored

---

## Visualizing Memory

```c
int x = 24;
char y = 'a';
int scores[7] = {-19, 8, 0, 1, 15, 3, 8};
scores[1] = 42;
```

Memory layout for this program will have:

* `x` and `y` stored at separate addresses
* `scores` occupying a block of 7 contiguous integers

---

## Getting the Address of a Variable

Use the `&` operator:

```c
#include <stdio.h>
int main() {
    int x, y;
    printf("Address of x: %p\n", &x);
    printf("Address of y: %p\n", &y);
    return 0;
}
```

Output will show hexadecimal memory addresses.

---

## What is a Pointer?

A **pointer** is a variable that stores the address of another variable.

### Declaration:

```c
int *ptr; // ptr can point to an int
```

### Assign Address:

```c
int k = 7;
ptr = &k; // ptr points to k
```

---

## Dereferencing a Pointer

To get or modify the value stored at the pointer's address, use the `*` operator:

```c
int a = *ptr;     // Read value
*ptr = 3;         // Modify value
```

### Comparison:

```c
int k = 7;
printf("%d", k);     // 7
int *p = &k;
printf("%d", *p);   // 7 (dereferenced value)
```

---

## Practice Exercise

```c
int num = 17;
int *p_num = &num;
printf("%d", *p_num); // 17

num = 14;
int x = *p_num;     // x = 14
*p_num = -7;        // num = -7

printf("%d", x);     // 14
printf("%d", num);   // -7
```

---

## Summary (Pointers)

```c
int *p_num;       // declaration
p_num = &x;       // point to x
a = 15 + *p_num;  // dereference
```

---

## Pass by Value vs Pass by Reference

### Pass by Value

The function gets a copy of the variable's value.

```c
void foo(int x, int y) {
    y = 10;
    printf("%d %d\n", x, y);
}

int main() {
    int x = 1, y = 2;
    foo(y, x);             // Output: 2 10
    printf("%d %d\n", x, y); // Output: 1 2
}
```

### Pass by Reference

The function receives the address of the variable.

```c
void foo(int *x, int *y) {
    *y = 10;
    printf("%d %d\n", *x, *y);
}
```

---

## Function with Pointer Arguments

### Declaration

```c
return_type function_name(type1 *arg1, type2 arg2, type3 *arg3) {
    // use *arg1, arg2, *arg3
    return result;
}
```

---

## Why Pass by Reference?

* Modify caller's variables directly
* Avoid copying large data structures (e.g., arrays)

### Example

```c
void func1(int a, char *b, float *c) {
    printf("%d %c %.2f\n", a, *b, *c);
    a = 60;
    *b = 'm';
    *c = 9.6;
}

int main() {
    int num1 = 5;
    float num2 = -4.78;
    char char1 = 'a';
    func1(num1, &char1, &num2);
    printf("%d %c %.2f\n", num1, char1, num2);
    return 0;
}
```

Output:

```
5 a -4.78
5 m 9.60
```

---

## Example: Swap Values

### Incorrect Version (Pass by Value)

```c
void swap(int x, int y) {
    int temp = x;
    x = y;
    y = temp;
}
```

### Correct Version (Pass by Reference)

```c
void swap(int *x, int *y) {
    int temp = *x;
    *x = *y;
    *y = temp;
}

int main() {
    int a = 5, b = 10;
    swap(&a, &b);
    printf("x=%d y=%d\n", a, b); // Output: x=10 y=5
}
```

---

## Final Exercise

```c
int func1(int *num1, int num2, int *num3) {
    *num1 += 1;               // a = 2
    num2 += 2;                // num2 = 12
    *num3 += num2 + *num1 + 1; // c = 115
    printf("%d %d %d\n", *num1, num2, *num3);
    return *num1 + num2 + *num3;
}

int main() {
    int a = 1, b = 10, c = 100;
    int *ptr = &c;
    int result = func1(&a, b, ptr);
    printf("%d %d %d\n", a, b, c);     // 2 10 115
    printf("%d\n", result);            // 129
    return 0;
}
```

---

## Summary

* Use `*` to declare and dereference pointers
* Use `&` to obtain variable addresses
* Pass by reference allows functions to modify original values
* Always dereference before accessing values through a pointer
