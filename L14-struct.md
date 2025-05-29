# Fundamentals of Programming - Lecture 14

## Structure in C

### What is a Structure?

A **structure** in C is a user-defined data type that allows grouping variables of different types under a single name. This helps manage complex data more effectively.

```c
struct Date {
    int month;
    int day;
    int year;
};
```

Structures are used to represent real-world entities like books, dates, points, and records.

---

## Structure Declaration and Initialization

### Declaration

```c
struct Point {
    int x;
    int y;
};

struct Point p1, p2;
```

### Initialization

```c
struct Point p1 = {3, 4};
```

You can also assign values member-wise:

```c
p1.x = 3;
p1.y = 4;
```

---

## Accessing Members

Use the dot operator `.` to access members of a structure.

```c
printf("x = %d, y = %d", p1.x, p1.y);
```

---

## Example: Date Structure

```c
#include <stdio.h>

struct Date {
    int day;
    int month;
    int year;
};

int main() {
    struct Date d1 = {1, 1, 1999};
    struct Date d2;
    d2.day = 25;
    d2.month = 12;
    d2.year = 2019;

    printf("%d-%d-%d\n", d1.day, d1.month, d1.year);
    printf("%d-%d-%d\n", d2.day, d2.month, d2.year);
    return 0;
}
```

---

## Exercise: Book Structure

Create a structure for a book:

```c
struct Book {
    int book_id;
    char title[51];
    char author[51];
    int num_pages;
};
```

### Example Input/Output:

```c
#include <stdio.h>
#include <string.h>

int main() {
    struct Book b1;
    scanf("%d", &b1.book_id);
    getchar();
    fgets(b1.title, 51, stdin);
    fgets(b1.author, 51, stdin);
    scanf("%d", &b1.num_pages);

    printf("Book(#%d) named %s authored by %s (%d pages)\n",
           b1.book_id, b1.title, b1.author, b1.num_pages);
    return 0;
}
```

---

## Structure Copy

Use `=` to copy structures.

```c
struct Account {
    int id;
    char name[20];
    float amount;
};

acc2 = acc1;  // Copies all member values
```

### Example

```c
acc2.id = 2;
acc2.amount -= 100;
acc2.name[strlen(acc2.name)-1] = 'A';
```

---

## Why Use Structures?

* Groups multiple variables
* Clean code
* Easy data management
* Ideal for programs dealing with entities like students, products, etc.

---

## Array of Structures

```c
struct Item {
    int id;
    char name[16];
    int qty;
    float price;
};

struct Item items[3] = {
    {1, "Lipton", 21, 20},
    {2, "Lay's", 7, 30},
    {3, "Pringles", 14, 55}
};
```

### Loop Through:

```c
for (int i = 0; i < 3; i++) {
    printf("%d %s %d %.2f\n", items[i].id, items[i].name, items[i].qty, items[i].price);
}
```

---

## Structure in Functions

### As a Parameter

```c
float calEuclidDist(struct Point p1, struct Point p2) {
    return sqrt(pow(p2.x - p1.x, 2) + pow(p2.y - p1.y, 2));
}
```

### As a Return Value

```c
struct Point calMidPoint(struct Point p1, struct Point p2) {
    struct Point mid;
    mid.x = (p1.x + p2.x)/2.0;
    mid.y = (p1.y + p2.y)/2.0;
    return mid;
}
```

---

## Structure within Structure

```c
struct Date {
    int day, month, year;
};

struct Item {
    int id;
    char name[16];
    int qty;
    float price;
    struct Date restock;
};
```

### Access Nested Members:

```c
an_item.restock.day = 1;
```

---

## typedef in Structures

```c
struct Date {
    int month, day, year;
};
typedef struct Date DATE;

DATE d1, d2;
```

This allows easier usage without repeating `struct` every time.

---

## Summary

* Structures allow grouping related data.
* `.` operator is used to access members.
* Arrays and functions work seamlessly with structs.
* Nested structs and `typedef` improve modularity and readability.
