---
title: "All Data-structures in C"
draft: false
---

C++ is cool, so let's implement all data structures in C. Now I will be a little lazy and not implement primitive data strucutures coz am lazy.

## Table of Contents
- [Table of Contents](#table-of-contents)
- [Lists](#lists)
  - [Linked List](#linked-list)
    - [Basic operations](#basic-operations)

## Lists
### Linked List
```C
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};
typedef struct Node Node;
```

#### Basic operations
```C
// Insert at beginning
void insert_beginning(Node** head, int data) {
    Node* new_node = calloc(1, sizeof(Node));
    new_node->data = data;
    new_node->next = *head;
    *head = new_node;
}

// Insert at end
void insert_end(Node **head, int data) {
    Node* new_node = calloc(1, sizeof(Node));
    new_node->data = data;
    new_node->next = NULL;
    if (*head == NULL) {
        *head = new_node;
        return;
    }
    Node* last = *head;
    while (last->next != NULL) {
        last = last->next;
    }
    last->next = new_node;
}

// Deletion
void delete_node(Node** head, int data) {
    Node* temp = *head, *prev;
    if (temp != NULL && temp->data == data) {
        *head = temp->next;
        free(temp);
        return;
    }
    while (temp != NULL && temp->data != data) {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL) {
        return;
    }
    prev->next = temp->next;
    free(temp);
}
```

The time complexities of these operations are as follows (average and worst are same for linked list)
| Operation              | Time Complexity |
| ---------------------- | --------------- |
| Access                 | O(n)            |
| Search                 | O(n)            |
| Insertion at beginning | O(1)            |
| Insertion at end       | O(n)            |
| Deletion               | O(1)            |