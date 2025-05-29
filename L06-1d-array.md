# Fundamentals of Programming - Lecture 6

## One-Dimensional Arrays in C

### What is a 1D Array?

A **one-dimensional array** (1D array) is a list of values that:

* Belong to the **same data type**
* Are stored under a **single group name**
* Are stored **consecutively in memory**
* Can be accessed using an **index** (an integer value)

### Example:

```c
int grades[5] = {98, 87, 92, 79, 85};
```

This declares an integer array named `grades` with 5 elements.

You can access each element using index notation:

```c
grades[0];  // First element (98)
grades[1];  // Second element (87)
```

Note: Array indexing in C starts from **0**.

---

## Declaring Arrays

### Syntax:

```c
datatype array_name[size];
```

### Examples:

```c
int grades[5];
char codes[4];
```

### Important Notes:

* Size should be **a constant or known at compile-time**.
* Can be defined using constants:

```c
#define N 5
int grades[N];
```

* Using variables (C99 and later):

```c
int n = 5;
int grades[n];
```

* For runtime sizes:

```c
int n;
scanf("%d", &n);
int grades[n];
```

---

## Array Indexing

* Indexing starts at **0** and ends at **N - 1**
* Use square brackets: `array_name[index]`
* Index must evaluate to an **integer** within bounds

### Examples:

```c
int a[3] = {1, 2, 3};
printf("%d", a[0]);  // prints 1
```

### Invalid access:

```c
a[3];  // out of bounds! undefined behavior
```

---

## Using Indexed Variables

Array elements behave like regular variables.

### Examples:

```c
int grades[5];
grades[0] = 98;
grades[1] = grades[0] - 11;
grades[2] = 2 * (grades[0] - 6);
```

### Equivalent code without arrays:

```c
int grade1 = 98;
int grade2 = grade1 - 11;
int grade3 = 2 * (grade1 - 6);
```

---

## Array Initialization

### Method 1: Manual assignment

```c
int grades[5];
grades[0] = 98; grades[1] = 87; ...
```

### Method 2: Inline initialization

```c
int grades[5] = {98, 87, 92, 79, 85};
```

### Method 3: Partial initialization

```c
float length[7] = {8.8, 6.4};
// remaining elements set to 0.0
```

### Method 4: Implicit size

```c
int scores[] = {10, 20, 30};  // size inferred to be 3
```

---

## Array Declaration vs. Initialization

```c
int n1 = 5;
int array1[n1];           // OK (variable size)
int array2[n1] = {0};      // Error (cannot initialize variable-length array)
int array3[] = {0};        // OK (size inferred)
#define N 5
int array4[N] = {0};       // OK
```

---

## Looping through Arrays

Arrays and loops go hand in hand for:

* Initialization
* Access
* Processing

### Example:

```c
int arr[5] = {5, 3, 6, 8, -7};
int sum = 0;
for (int i = 0; i < 5; i++) {
    sum += arr[i];
}
printf("%d", sum); // Output: 15
```

---

## User Input with Arrays

```c
int arr[5];
int sum = 0;
for (int i = 0; i < 5; i++) {
    scanf("%d", &arr[i]);
    sum += arr[i];
}
float avg = sum / 5.0;
printf("%.2f", avg);
```

---

## Conditional Logic with Arrays

```c
int arr[8] = {9, 3, 4, 5, 2, 1, 7, 6};
int sum = 0, product = 1;

for (int i = 0; i < 8; i++) {
    if (arr[i] % 2 == 0) sum += arr[i];
    else product *= arr[i];
}
```

---

## Exercises: Code Tracing

### What is the output?

```c
int arr[5] = {2, 4, 6, 0, 1};
for (int i = 0; i < 5; i++) {
    printf("%d %d\n", i, arr[i]);
}
```

### Reversed Order

```c
for (int i = 1; i <= 5; i++) {
    printf("%d %d\n", i, arr[5 - i]);
}
```

### Access Violation

```c
for (int i = 0; i <= 5; i++) {
    printf("%d %d\n", i, arr[5 - i]); // arr[5] is invalid at i = 0
}
```

### Find Index of Zero

```c
int o = -1;
for (int i = 0; i < 5; i++) {
    if (arr[i] == 0) o = i;
}
printf("%d", o);  // Output: 3
```

---

## Practical Example: Sales Calculation

```c
#define N 3
float prices[N] = {1.5, 3.5, 2.0};
int units[N] = {4, 2, 3};
float sales = 0;
for (int i = 0; i < N; i++) {
    sales += prices[i] * units[i];
}
printf("%.2f", sales); // Output: 19.00
```

---

## Nested Loops with Arrays

```c
#define N 5
char alp[N] = {'A','B','C','D','E'};
int num[N] = {1,2,3,4,5};

for (int i = 0; i < N; i++) {
    for (int j = N-1; j >= 0; j--) {
        printf("%c%d ", alp[i], num[j]);
    }
    printf("\n");
}
```

### Output:

```
A5 A4 A3 A2 A1
B5 B4 B3 B2 B1
...
```

---

## Summary

* Arrays group related values under one name.
* Access using indexes: `array[index]`
* Index starts from 0 and ends at `size-1`
* Use loops to manipulate array values efficiently.
* Pay attention to array bounds to avoid undefined behavior.
* Initialization can be full, partial, or runtime-based.

Practice writing code to:

* Traverse arrays
* Accumulate or compare values
* Apply conditions inside loops
