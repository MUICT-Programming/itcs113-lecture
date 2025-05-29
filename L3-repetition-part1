# Fundamentals of Programming - Lecture 3

## Flow Controls in C Programming

Flow control refers to the order in which individual statements, instructions, or function calls are executed or evaluated. In C, control flow is classified into four main structures:

### 1. Sequential

* The default mode: statements are executed one after the other, in the order they appear.

```c
int main() {
    statement1;
    statement2;
    statement3;
    return 0;
}
```

### 2. Selection

* Used to choose different paths of execution depending on the outcome of a condition.

#### `if` Statement:

```c
if (condition) {
    // block of code if condition is true
}
```

#### `if-else if-else` Chain:

```c
if (expression1) {
    // code
} else if (expression2) {
    // code
} else {
    // default code
}
```

#### Example:

```c
int age = 78;
int discount = 0;
if (age > 60)
    discount = 20;
```

#### `switch` Statement:

* Evaluates an integer or character expression and executes code based on matching case.

```c
switch (value) {
    case 1:
        // code block
        break;
    case 2:
        // code block
        break;
    default:
        // default block
}
```

### 3. Repetition (Loops)

Used to repeat a block of code multiple times.

#### Key Components:

* **Initialization:** defines and initializes the loop control variable
* **Condition:** evaluated before each iteration; if true, loop continues
* **Alteration:** updates the loop control variable
* **Body:** the code to be repeated

#### Example:

```c
int i = 1;
while (i <= 10) {
    printf("%d ", i);
    i++;
}
```

### 4. Invocation

* Function calls which can alter the control flow by jumping to a different set of instructions.

---

## `while` Loop

### Syntax:

```c
while (condition) {
    // code block
}
```

### Example:

```c
int i = 1;
while (i <= 100) {
    printf("%d ", i);
    i++;
}
```

* Use when the number of iterations is not known in advance.

### Reverse Counting:

```c
int i = 100;
while (i >= 1) {
    printf("%d ", i);
    i--;
}
```

---

## `for` Loop

### Syntax:

```c
for (initialization; condition; alteration) {
    // code block
}
```

### Example:

```c
for (int i = 1; i <= 100; i++) {
    printf("%d ", i);
}
```

### Decreasing Order:

```c
for (int i = 20; i >= 0; i -= 5) {
    printf("%d ", i);
}
```

---

## Comparing `for` and `while`

| Feature        | `for` Loop                             | `while` Loop                    |
| -------------- | -------------------------------------- | ------------------------------- |
| Use case       | When the number of iterations is known | When the number is unknown      |
| Initialization | Done in loop header                    | Done before loop                |
| Alteration     | In header                              | Inside loop body                |
| Best for       | Counting loops                         | Conditional, event-driven loops |

---

## Example Exercises

### Pattern: 1, 3, 5, 7, 9

```c
for (int i = 1; i <= 9; i += 2) {
    printf("%d ", i);
}
```

### Pattern: 10, 8, 6, 4, 2

```c
int i = 10;
while (i >= 2) {
    printf("%d ", i);
    i -= 2;
}
```

### Pattern: a, b, c, ..., k

```c
for (int i = 0; i <= 10; i++) {
    printf("%c ", i + 'a');
}
```

---

## Using `while` for Input Processing

### Example: Accumulating Sum

```c
int sum = 0, num, i = 1;
while (i <= 10) {
    scanf("%d", &num);
    sum += num;
    printf("%d: %d\n", i, sum);
    i++;
}
```

### Sentinel-controlled Loop

Keep receiving input until a negative number is entered.

```c
int n = 0, sum = 0;
while (n >= 0) {
    scanf("%d", &n);
    if (n >= 0) sum += n;
}
printf("Sum = %d\n", sum);
```

---

## Infinite Loops Warning

Be careful with conditions:

```c
for (int i = 1; i > 0; i++) {
    printf("%d ", i); // Will never end
}
```

* Stop execution using Ctrl + C or STOP in IDE.
