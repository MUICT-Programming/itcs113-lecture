# Fundamentals of Programming - Lecture 12

## Pointers in C - Part 2

### Topics Covered

* Pointer declaration and usage
* Pass by reference
* Pointers and arrays
* Passing arrays to functions

---

## Pointer Basics

### Declaring a Pointer

```c
int *ptr; // ptr is a pointer to an int
```

### Pointing to a Variable

```c
int k = 10;
ptr = &k; // ptr now stores the address of k
```

### Dereferencing a Pointer

```c
*ptr = 3;   // modifies the value of k
int x = *ptr; // x = 3
```

---

## Pass by Reference

When a function receives pointers to variables, it can modify the original values.

### Example:

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

### Output:

```
5 a -4.78
5 m 9.60
```

---

## Example: Swapping Two Values

### Pass by Reference Version

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
    return 0;
}
```

---

## Using Pointers with Arrays

### Array Basics

```c
int lab_scores[15];
```

Array variable names decay to pointers:

```c
int *ptr1 = lab_scores;
int *ptr2 = &lab_scores[0];
```

### Pointer Arithmetic

```c
*(lab_scores + 1) == lab_scores[1]
```

---

## Accessing Array Elements via Pointer

```c
int lab_scores[15] = {...};
int *ptr = &lab_scores[0];

for (int i = 0; i < 15; i++) {
    printf("%d ", *(ptr + i)); // or ptr[i]
}
```

---

## Full Example

```c
int nums[10] = {10, 315, 72, 73, 34, 25, 61, 72, 18, -9};
int *p_num = nums;

for (int i = 0; i < 10; i++) {
    printf("%d ", *(p_num + i));
}
```

### Output:

```
10 315 72 73 34 25 61 72 18 -9
```

---

## Exercise: Pointer Arithmetic

```c
int nums[5] = {-4, 15, 91, 34, 0};
int *ptr_1 = &nums[0];
int *ptr_2 = &nums[4];
int *ptr_3 = nums;

printf("%d\n", *ptr_1);     // -4
printf("%d\n", *(ptr_1 + 3)); // 34
printf("%d\n", ptr_1[1]);    // 15
printf("%d\n", nums[1]);     // 15
printf("%d\n", *nums);       // -4
printf("%d\n", *ptr_3);      // -4
printf("%d\n", *ptr_2);      // 0
printf("%d\n", *(ptr_2 - 2)); // 91
printf("%d\n", *(ptr_2 + 1)); // undefined (out of bounds)
```

---

## Passing Arrays to Functions

```c
int find_max(int *arr, int n_elems) {
    int max = *arr;
    for (int i = 1; i < n_elems; i++) {
        if (*(arr + i) > max) {
            max = *(arr + i);
        }
    }
    return max;
}

int main() {
    int nums[5] = {4, -5, 7, 99, 0};
    printf("%d", find_max(nums, 5)); // Output: 99
    return 0;
}
```

Or using array notation:

```c
int find_max(int arr[], int n_elems);
```

---

## Exercise: Square Array Elements

```c
void func1(int *arr, int n) {
    for (int i = 0; i < n; i++) {
        arr[i] = arr[i] * arr[i];
    }
}

int main() {
    int arr[5] = {-5, 3, 4, 1, 8};
    func1(arr, 5);

    for (int i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```

### Output:

```
25 9 16 1 64
```

---

## Exercise: Compute Sum

### Starter Code

```c
#include <stdio.h>

int sum(int *arr, int size);

int main() {
    int n = 5;
    int arr[n];
    for (int i = 0; i < n; i++) {
        arr[i] = i * i;
    }
    printf("%d", sum(arr, n));
    return 0;
}
```

### Function Definition

```c
int sum(int *arr_ptr, int size) {
    int total = 0;
    for (int i = 0; i < size; i++) {
        total += *(arr_ptr + i);
    }
    return total;
}
```

---

## Summary

* Use `*` to dereference, `&` to get addresses
* Use pointers to manipulate arrays
* Passing arrays as function arguments uses pointer semantics
* Use `ptr[i]` or `*(ptr + i)` to access elements
