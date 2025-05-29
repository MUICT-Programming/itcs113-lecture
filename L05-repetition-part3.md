# Fundamentals of Programming - Lecture 5

## Advanced Repetition and Nested Loops

### Today's Topics

* Nested Loops
* Step-by-step pattern analysis
* Multiple inner loops
* Printing patterns with loops

---

## Recap: Be Considerate of Shared Resources

Before testing with `run.sh`, always run:

```sh
gcc main.c -o main && ./main
```

Avoid infinite loops which can generate massive output files that clog shared systems.

---

## Introduction to Nested Loops

A **nested loop** is a loop inside another loop.

### Example:

```c
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= i; j++) {
        printf("* ");
    }
    printf("\n");
}
```

This prints a right-angled triangle pattern:

```
*
* *
* * *
```

### General Form:

```c
for (int i = ...) {
    for (int j = ...) {
        // body
    }
}
```

---

## Step-by-Step Pattern Analysis

Let’s analyze the relationship between `i` (row) and `j` (column):

| i | j values   |
| - | ---------- |
| 1 | 1          |
| 2 | 1, 2       |
| 3 | 1, 2, 3    |
| 4 | 1, 2, 3, 4 |
| n | 1 to n     |

We observe:

* Outer loop variable `i` increases from 1 to `n`
* Inner loop variable `j` runs from 1 to `i`

### Code Template:

```c
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= i; j++) {
        printf("%d ", i-1);
    }
    printf("\n");
}
```

This prints:

```
0
1 1
2 2 2
3 3 3 3
...
```

---

## Analyzing Multiple Patterns

Suppose we want to combine multiple inner loops in one row:

Example output:

```
0 - - - -
0 1 - - -
0 1 2 - -
...
```

We identify three components:

* Triangle of increasing numbers
* Upside-down triangle of `-`

### Code Example:

```c
int n = 5;
for (int i = 1; i <= n; i++) {
    // Numbers
    for (int j = 0; j < i; j++) {
        printf("%d ", j);
    }
    // Dashes
    for (int k = n - i; k > 0; k--) {
        printf("- ");
    }
    printf("\n");
}
```

Output:

```
0 - - - -
0 1 - - -
0 1 2 - -
...
```

---

## Multiple Inner Loops Template

```c
int n = 5;
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= i; j++) {
        printf("%d ", i-1);
    }
    for (int k = n-i; k >= 1; k--) {
        printf("- ");
    }
    printf("\n");
}
```

Produces:

```
0 - - - -
1 1 - - -
2 2 2 - -
3 3 3 3 -
4 4 4 4 4
```

---

## Practice Exercise

Write a nested loop to produce the following pattern:

```
1
2 2
3 3 3
4 4 4 4
5 5 5 5 5
```

### Solution:

```c
int n = 5;
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= i; j++) {
        printf("%d ", i);
    }
    printf("\n");
}
```

---

## Summary

* Use nested loops to construct rows and columns.
* Observe how inner loops vary with outer loop variable.
* Combine inner loops to form complex patterns.
* Always verify how variables like `i` and `j` map to the output format.

---

## Lab Tip

Test your loop logic with small values of `n` (like 3 or 4) before scaling.
Use `printf` debugging inside loops to check variable values.
