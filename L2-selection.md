# Fundamentals of Programming - Lecture 2

## Today’s Topics

* RECAP
* Relational and Logical Expressions
* if-else statement
* switch statement
* Ternary operator
* Symbolic constants

---

## RECAP: C Program Basics and I/O

### Structure of a Basic C Program

```c
#include <stdio.h>
int main() {
    // Print greeting
    printf("Hello World");
    return 0;
}
```

* `#include <stdio.h>`: Includes the standard input/output library.
* `main()`: Entry point of the program.
* Use comments (`//` or `/* */`) to explain code.
* All C programs must contain `main()`.

### Input and Output

```c
int a;
scanf("%d", &a);
printf("%d", a);
```

* `%d`, `%f`, `%c`: Format specifiers for `int`, `float`, and `char`.
* `scanf()` requires the address of the variable to store the input.

---

## Variables: Initialization and Assignment

### Initialization

```c
int width = 10;
int height = 5, volume = 2;
```

* Initialization assigns an initial value at the time of declaration.

### Assignment

```c
sum = 3 + 7;
diff = 15 - 6;
product = 0.05 * 14.6;
```

* Assigns value from right-hand expression to the variable.
* All variables used in expressions should be initialized beforehand.

---

## Relational and Logical Operators

### Relational Operators

* `<`, `>`, `<=`, `>=`, `==`, `!=`
* Compares two values and returns 1 (true) or 0 (false)
* **Note:** `==` is not the same as `=`

### Logical Operators

* `&&` (AND): true if both operands are true
* `||` (OR): true if at least one operand is true
* `!` (NOT): negates the truth value

### Example

```c
if (x > 0 && x % 2 == 1) {
    printf("Positive odd number\n");
}
```

---

## Increment and Decrement

### Postfix vs Prefix

```c
int x = 10;
printf("%d", x++); // prints 10, then x = 11
printf("%d", ++x); // x = 12, then prints 12
```

* `x++`: returns current value, then increments
* `++x`: increments first, then returns value

---

## Writing Clear Code

* **Use meaningful variable names:** e.g., `netSalary`, `averageScore`
* **Comment your code:** explain non-obvious logic
* **Indent consistently:** enhances readability

---

## Flow Control: if and if-else

### Syntax

```c
if (condition) {
    // do something
} else {
    // do something else
}
```

* Executes different code blocks based on condition truth.

---

## Nested if-else

### Example: Grading System

```c
if (score >= 80)
    printf("Grade A");
else if (score >= 70)
    printf("Grade B");
else if (score >= 60)
    printf("Grade C");
else
    printf("Grade F");
```

* Used when multiple exclusive conditions are possible

---

## switch Statement

### Syntax

```c
switch (expression) {
    case 1:
        // code
        break;
    case 2:
        // code
        break;
    default:
        // fallback code
}
```

* `switch` compares `expression` to each `case` label.
* Without `break`, all cases after a match will execute (fall-through).

---

## Ternary Operator

### Syntax

```c
(condition) ? true_value : false_value;
```

* Concise if-else for assigning values

### Example

```c
int min = (a > b) ? b : a;
```

---

## Symbolic Constants

### Using `#define`

```c
#define PI 3.14
#define G 9.81
```

* Defined at the top of the file
* Cannot be changed during program execution

---

## Formatted Output

### printf Format

```c
printf("%10.2f", num); // right-aligned, 2 decimals
printf("%-10.2f", num); // left-aligned, 2 decimals
```

* `%10.2f`: total width = 10, precision = 2 digits after decimal point
* `-` aligns to the left
