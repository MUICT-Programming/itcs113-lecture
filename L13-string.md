# Lecture 13: Strings in C

## Topics Covered

* Initializing a string variable
* String input/output
* String library functions
* Looping through strings

---

## What is a String in C?

* A **string** is a sequence of characters enclosed in double quotes, e.g., `"Hello"`
* In C, a string is an **array of characters** terminated with the null character `\0`
* C does **not** have a built-in string data type

### Example:

```c
char name[20] = "Computer";  // Stored as: C o m p u t e r \0
```

---

## Declaring and Initializing Strings

### Method 1: Using string literals

```c
char date[] = "June 14";
```

### Method 2: Explicit character array

```c
char date[] = {'J','u','n','e',' ','1','4','\0'};
```

### Method 3: Specify size

```c
#define MAX_LEN 10
char date1[MAX_LEN+1] = "June 14";
char date2[MAX_LEN+1] = "May 14";
```

Note: The extra `+1` is for the null terminator `\0`.

---

## String Pointers vs Arrays

### Read-Only Pointer Initialization

```c
char *date = "June 14";
date[0] = 'J'; // Causes error or crash
```

### Mutable Array Initialization

```c
char date[] = "June 14";
date[0] = 'J'; // Allowed
```

---

## String Input and Output

### Common Functions

| Input       | Output      |
| ----------- | ----------- |
| `scanf()`   | `printf()`  |
| `fgets()`   | `puts()`    |
| `getchar()` | `putchar()` |

### `scanf()` Example

```c
char input_str[15];
scanf("%s", input_str);
printf("%s", input_str);
```

* Reads input until the first whitespace
* No `&` operator needed because `input_str` is already an address

### `fgets()` Example

```c
char input_str[15];
fgets(input_str, 15, stdin);
printf("%s", input_str);
```

* Reads up to `n-1` characters or until newline
* Retains `\n`, which can be removed using:

```c
char *pos;
if ((pos=strchr(input_str, '\n')) != NULL) *pos = '\0';
```

### `getchar()` with Loop

```c
char input_str[15];
int i = 0;
char c = getchar();
while ((i < 14) && (c != '\n')) {
    input_str[i++] = c;
    c = getchar();
}
input_str[i] = '\0';
```

---

## String Library Functions

### Character-based (from `<ctype.h>`):

* `isalpha()`, `isupper()`, `islower()`, `isdigit()`
* `toupper()`, `tolower()`

### String-based (from `<string.h>`):

* `strlen(str)` - get length
* `strcpy(dest, src)` - copy
* `strcat(dest, src)` - concatenate
* `strcmp(s1, s2)` - compare strings
* `strchr(str, c)` - find first occurrence
* `strrchr(str, c)` - find last occurrence

### Safer Variants:

* `strncpy()`, `strncat()`, `strncmp()`

---

## Comparing Strings

### `strcmp()` Return Values:

* `0`: strings are identical
* `< 0`: str1 < str2
* `> 0`: str1 > str2

```c
int result = strcmp("Google", "Microsoft");
```

### Example using function

```c
void compare_string(char *s1, char *s2) {
    int res = strcmp(s1, s2);
    if (res == 0) printf("%s == %s\n", s1, s2);
    else if (res > 0) printf("%s > %s\n", s1, s2);
    else printf("%s < %s\n", s1, s2);
}
```

---

## Assigning and Copying Strings

### Invalid

```c
char str1[] = "Google";
char str2[] = "Microsoft";
str2 = str1; // Not allowed
```

### Use `strcpy()`

```c
strcpy(str2, str1);
```

Be cautious about buffer sizes to avoid overflow!

---

## Concatenating Strings

```c
char fname[20], lname[20], fullname[40];
scanf("%s", fname);
scanf("%s", lname);
strcpy(fullname, fname);
strcat(fullname, " ");
strcat(fullname, lname);
```

---

## Looping Through Strings

Use a `while` loop to process characters:

```c
char str[] = "This is a test.";
int i = 0;
while (str[i] != '\0') {
    if (str[i] == 'a') count++;
    i++;
}
```

Or use a `for` loop with `strlen(str)`:

```c
for (int i = 0; i < strlen(str); i++) { ... }
```

---

## Copying String Manually

```c
char str1[] = "This_is_a_very_long_string.";
char str2[20];
int i = 0;
while ((str1[i] != '\0') && (i < 19)) {
    str2[i] = str1[i];
    i++;
}
str2[i] = '\0';
```

---

## Replacing Characters

```c
char str[] = "Learning_C_is_fun!";
for (int i = 0; str[i] != '\0'; i++) {
    if (str[i] == '_') str[i] = ' ';
}
```

---

## Toggling Case of Characters

```c
char str[] = "Welcome_to_C_Programming!";
for (int i = 0; str[i] != '\0'; i++) {
    if (isalpha(str[i])) {
        if (islower(str[i])) str[i] = toupper(str[i]);
        else str[i] = tolower(str[i]);
    }
}
```

---

## Summary

* Strings in C are null-terminated character arrays
* Be careful with input methods to avoid buffer overflows
* Use library functions to manipulate strings effectively
* Use loops to process strings character-by-character

