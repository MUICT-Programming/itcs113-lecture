# Fundamentals of Programming - Lecture 7

## 2D Arrays in C

### Recap: 1D Arrays

A one-dimensional (1D) array is a linear list of values of the same type, accessible via index notation.

Example:

```c
int grades[5] = {98, 87, 92, 79, 85};
```

---

## Motivation for Multidimensional Arrays

Suppose you store lab scores for one student:

```c
int lab_scores[15];
```

Now imagine 38 students:

```c
int lab_scores1[15];
int lab_scores2[15];
...
int lab_scores38[15];
```

This is inefficient and unscalable.

---

## Multidimensional Arrays

Arrays with two or more dimensions. All elements must be the same type.

### Declaration

```c
// General form:
datatype arrayName[size_1][size_2];

// Example for 2D array:
int lab_scores[38][15];
```

* `lab_scores[student][lab]`
* You can also swap dimensions: `lab_scores[15][38]`

---

## 3D Arrays

Used when you need to store more complex data like:

* Different groups of students
* Time series per student and lab

```c
int lab_scores[38][15][2];
```

---

## Application Examples

| Structure | Application            |
| --------- | ---------------------- |
| 1D        | Grades, inputs         |
| 2D        | Tables, student scores |
| 3D        | Images, datasets       |
| 4D+       | Videos, time series    |

---

## 2D Array Concepts

A 2D array can be visualized as a table with rows and columns.

### Example:

```c
int lab_scores[38][15];
```

| Row\Col | 0 | 1 | ... | 14 |
| ------- | - | - | --- | -- |
| 0       |   |   |     |    |
| 1       |   |   |     |    |
| ...     |   |   |     |    |
| 37      |   |   |     |    |

Access element: `lab_scores[row][col]`

---

## Initialization

### Explicit Braces:

```c
int val[3][4] = {
    {8, 16, 9, 52},
    {3, 15, 27, 6},
    {14, 25, 2, 10}
};
```

### Implicit Braces:

```c
int val[3][4] = {8, 16, 9, 52, 3, 15, 27, 6, 14, 25, 2, 10};
```

Stored in **row-major** order.

---

## Quiz: What’s Inside?

```c
int grades1[3][3] = {9,6,8,7,10,3,10,9,9};
int grades2[2][4] = {{6,8,9,5},{10,3,7,5}};

printf("%d\n", grades1[0][2]);        // → 8
printf("%d\n", grades1[1][0] + grades1[0][1]); // → 7+6 = 13
printf("%d\n", grades1[1][1] + grades2[0][3]); // → 10+5 = 15
```

Note: `grades1[0][3]` is invalid! Index out-of-bounds.

---

## Looping with 2D Arrays

### Nested Loops Example

```c
int val[3][4] = {
    {8,16,9,52},
    {3,15,27,6},
    {14,25,2,10}
};

for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 4; j++) {
        printf("%d ", val[i][j]);
    }
    printf("\n");
}
```

### Output:

```
8 16 9 52
3 15 27 6
14 25 2 10
```

---

## Loop Column-wise

```c
for (int j = 0; j < 4; j++) {
    for (int i = 0; i < 3; i++) {
        printf("%d ", val[i][j]);
    }
    printf("\n");
}
```

### Output:

```
8 3 14
16 15 25
9 27 2
52 6 10
```

---

## Summary

* Use 2D arrays to model matrices or tables
* Access with `array[row][col]`
* Use nested loops to process all elements
* Initialize arrays with or without braces
* Beware of index out-of-bound errors

### Tip:

Always know which loop represents row and which column when traversing!
