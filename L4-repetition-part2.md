# Fundamentals of Programming - Lecture 4

## Today's Topics

* RECAP: Loop structures (`for`, `while`, `do-while`)
* Input data validation
* Loop control: `break` and `continue`

---

## Basic Loop Structure in C

A loop has four essential components:

1. **Initialization**: Prepares the loop control variable.
2. **Condition**: A relational expression; loop continues if `true`.
3. **Body**: The repeating statements.
4. **Alteration**: Changes the control variable to approach termination.

Example of a `while` loop:

```c
int i = 1;
while (i <= 100) {
    printf("%d ", i);
    i = i + 1;
}
```

---

## `for` Loop

The `for` loop is concise and typically used when the number of iterations is known in advance.

Example:

```c
char i;
for (i = 'a'; i <= 'z'; i++) {
    printf("%c ", i);
}
```

---

## Comparing `for` and `while`

```c
// using while
int count = 1;
while (count <= 10) {
    printf("%d", count);
    count++;
}

// using for
for (int count = 1; count <= 10; count++) {
    printf("%d", count);
}
```

* Use `for` when you **know** the number of iterations.
* Use `while` when the repetition count is **unknown**.

---

## Practical Examples

### Example 1: Count Odd Digits Until 'q'

```c
int counter = 0;
char n = '0';
while(n != 'q' && n >= '0' && n <= '9') {
    scanf(" %c", &n);
    if (n >= '0' && n <= '9') {
        int num = n - '0';
        if (num % 2 == 1) counter++;
    }
}
```

### Example 2: Find Minimum of 10 Floats

```c
float input;
float min;
for (int i = 0; i < 10; i++) {
    printf("Input (%d of 10):", i+1);
    scanf("%f", &input);
    if (i == 0 || input < min)
        min = input;
}
```

### Example 3: Print 0 to N

```c
int N;
scanf("%d", &N);
for (int i = 0; i <= N; i++) {
    printf("%d ", i);
}
```

---

## `do-while` Loop

Ensures the loop runs at least once, since the condition is evaluated after the loop body.

### Syntax

```c
do {
    // statements
} while (condition);
```

### Example

```c
int i = 5;
do {
    printf("%d ", i);
    i--;
} while (i > 0);
```

### Input Validation Example

```c
int n;
do {
    printf("Enter a non-negative number: ");
    scanf("%d", &n);
} while (n < 0);
printf("Input number: %d\n", n);
```

---

## Summary of Loops

| Loop Type  | Use Case               | Evaluation Point |
| ---------- | ---------------------- | ---------------- |
| `for`      | Known iterations       | Pre-condition    |
| `while`    | Unknown iterations     | Pre-condition    |
| `do-while` | Must run at least once | Post-condition   |

---

## Choosing a Loop

Ask:

* Do you need repetition?
* Do you know the number of repetitions?

  * Yes: Use `for` or `while`
  * No: Use `while` or `do-while`
* Do you need to run the loop at least once? Use `do-while`

---

## Loop Examples

### Print Patterns:

```c
// Print 1 3 5 7 9
for (int i = 1; i <= 9; i += 2) printf("%d ", i);

// Print 10 8 6 4 2
for (int i = 10; i >= 2; i -= 2) printf("%d ", i);

// Print letters a to k
for (char c = 'a'; c <= 'k'; c++) printf("%c ", c);

// Print 1, 2, 4, 8, 16, 32
for (int i = 1; i <= 32; i *= 2) printf("%d ", i);
```

---

## Loop Control Statements

### `break`

Terminates a loop immediately.

```c
while (1) {
    scanf("%d", &n);
    if (n < 0) break;
    sum += n;
}
```

### `continue`

Skips the rest of the loop body and proceeds with the next iteration.

```c
for (int i = 0; i < 10; i++) {
    scanf("%d", &n);
    if (n <= 0) continue;
    sum += n;
}
```

---

## Example: Sum Until Negative

```c
int sum = 0, num = 0;
while (1) {
    printf("Enter a number: ");
    scanf("%d", &num);
    if (num < 0) break;
    sum += num;
}
printf("Sum: %d\n", sum);
```

---

## Final Thoughts

* Always define clear loop control variables.
* Use input validation to make programs more robust.
* Choose the right type of loop for the situation.
* Understand `break` and `continue` to control loop flow effectively.
