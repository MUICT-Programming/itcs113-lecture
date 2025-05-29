# Fundamentals of Programming - Lecture 10

## Variable Scope in C

### Agenda

* Function Scope
* Variable Scope
* Guidelines for Declaring Variables

---

## Function Scope: Blocks

Each function in C has its own **block scope**. This means variables declared within a function are only accessible during its execution.

### Example:

```c
#include <stdio.h>

void foo() {
    int o = 100;
}

int main() {
    foo();
    printf("%d", o); // Error: 'o' is not visible here
    return 0;
}
```

Explanation: The variable `o` declared in `foo()` is not accessible in `main()`.

---

## Function Scope: Variable Accessibility

Variables declared inside a function:

* Exist only while the function is running
* Are destroyed when the function exits
* Cannot be accessed from another function

### Example:

```c
#include <stdio.h>

void foo() {
    int o = 100;
}

int main() {
    foo();
    printf("%d", o); // Error
    return 0;
}
```

Another example:

```c
#include <stdio.h>

void foo() {
    o++; // Error: 'o' not declared here
}

int main() {
    int o = 10;
    foo();
    return 0;
}
```

### Function Parameters as Local Variables

```c
#include <stdio.h>

void foo(int x) {
    printf("%d", x);
}

int main() {
    foo(42);
    printf("%d", x); // Error: x not in scope
    return 0;
}
```

---

## Function Scope: Pass by Value

In C, arguments are passed **by value**, meaning the function gets a copy of each argument.

### Example:

```c
#include <stdio.h>

void foo(int x, int y) {
    y = 10;
    printf("%d %d\n", x, y);
}

int main() {
    int x = 1, y = 2;
    foo(y, x); // output: 2 10
    printf("%d %d\n", x, y); // output: 1 2
    return 0;
}
```

Modifications inside `foo` do not affect `main`'s variables.

---

## Exercises (Function Scope)

### Exercise 1:

```c
void foo(int x, int c) {
    printf("%d\n", x);
    x = 1000;
    c = 4;
    printf("%d\n", x);
}

int main() {
    int x = 42, d = 10;
    foo(x, d);
    printf("%d\n", x);
    printf("%d\n", d);
    return 0;
}
```

**Output:**

```
42
1000
42
10
```

### Exercise 2:

```c
void foo(int x){
    printf("%d", y);
}

int main(){
    int y = 42;
    foo(y); // Error: y not in scope of foo
    return 0;
}
```

### Exercise 3:

```c
int is_odd(int i){
    return i % 2 == 1;
}

void foo(){
    int o = 1000;
}

int main(){
    int o = 0;
    for (int i = 0; i < 5; i++) {
        if (is_odd(i)) o += i;
    }
    foo();
    printf("%d\n", o); // Output: 4
    return 0;
}
```

---

## Variable Scope

There are three types of variable scope in C:

1. **Global Variables**: Declared outside any function
2. **Local Variables**: Declared inside a function or block
3. **Formal Parameters**: Declared in function headers, act like local variables

### Example:

```c
#include <stdio.h>
int foo; // Global variable

int main() {
    float x; // Local variable
}

void foo(char param) {
    // param is a formal parameter (local)
}
```

---

## Code Blocks and Scope

Each pair of curly braces `{}` defines a new block and scope.
Common constructs that introduce new scopes:

* `if`, `else`
* `for`
* `while`
* Function definitions

### Example:

```c
#include <stdio.h>

void foo(int i) {
    if (i > 0) {
        int a = 0; // Exists only in this if block
    }
}

int main() {
    int a = 1, b = 2;
    for (int i = 0; i < 4; i++) {
        b = 10;
    }
    return 0;
}
```

---

## Variable Override (Shadowing)

If two variables have the same name, the **most local** one is used.

### Example:

```c
#include <stdio.h>
char a = 'a'; // Global variable

int main() {
    int a = 10; // Local variable shadows global
    printf("%d", a); // Output: 10
    return 0;
}
```

---

## Guidelines on Declaring Variables

* **Avoid global variables** unless absolutely necessary
* Do **not** use the same name as a function for a variable
* Declare variables **early** in a function for readability

---

## Scope Visualization Example

```c
#include <stdio.h>
char a = 'b';

int main() {
    int b = 1;
    for (int i = 0; i < 4; i++) {
        int c = 10;
        a++;
    }
    printf("%d %d", i, c); // Error: i and c not visible here
    return 0;
}
```

### Output:

```
Error: i and c are out of scope
```

---

## Summary

* Variables exist only within their declared scope
* Variables are destroyed when leaving their scope
* Variables in different scopes can share the same name
* Use most local declaration to avoid unintended overrides
* Understand scope rules to write safe and maintainable code

---

## Practice Exercises

### Exercise 4:

```c
#include <stdio.h>
char m = 'c';
float n = 1.0;
int o = 9;

int main() {
    int i = 20;
    int m = 1;
    for (int i = 0; i < 4; i++) {
        o = 10;
        m++;
        m = 20;
        n = m + o;
    }
    o = m + i; // Evaluate values of m, n, o here
    return 0;
}
```

### Exercise 5:

```c
#include <stdio.h>
int x = 1;
int main() {
    printf("%d %d", x, y); // Error: y declared after main
    return 0;
}
int y = 2;
```

### Exercise 6:

```c
#include <stdio.h>
int x = 1;

int foo() {
    x++; // modifies global x
    return x + 10;
}

int main() {
    int y = foo();
    int z = foo();
    printf("%d %d %d", x, y, z); // x = 3, y = 12, z = 13
    return 0;
}
```
