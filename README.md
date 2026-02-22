C Program: Queue Implementation Using Linked List

This project demonstrates how to implement a *Queue Data Structure using a Linked List* in C.

Unlike array-based queues, this implementation uses *dynamic memory allocation*, allowing the queue to grow until system memory is exhausted.

---

Description

The program:

* Defines a queue using a struct Node
* Maintains two pointers:

  * front → points to the first element
  * rear → points to the last element
* Implements:

  * *Enqueue (Insertion)*
  * *Dequeue (Deletion)*
  * *Display*
* Handles:

  * *Heap Overflow* (when memory allocation fails)
  * *Queue Underflow* (when queue is empty)

This example is ideal for students learning *Queues in Data Structures using Linked Lists*.

---

Source Code

c

#include <stdio.h>

#include <stdlib.h>

// Define structure for node

struct Node {
    int data;
    struct Node* next;
};

// Declare front and rear pointers

struct Node* front = NULL;
struct Node* rear = NULL;

// Check if queue is empty

int isEmpty() {
    return (front == NULL);
}

// Enqueue operation

void enqueue(int value) {
    
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    if (newNode == NULL) {
        
        printf("Heap Overflow!\n");
        return;
    }

    newNode->data = value;
    newNode->next = NULL;

    if (isEmpty()) {
        front = rear = newNode;
    } else {
        rear->next = newNode;
        rear = newNode;
    }

    printf("Inserted: %d\n", value);
}

// Dequeue operation

void dequeue() {
    
    if (isEmpty()) {
        printf("Queue is Empty!\n");
        return;
    }

    struct Node* temp = front;
    printf("Deleted: %d\n", front->data);

    front = front->next;

    if (front == NULL) {
        rear = NULL;
    }

    free(temp);
}

// Display queue

void display() {
    
    if (isEmpty()) {
        printf("Queue is Empty!\n");
        return;
    }

    struct Node* temp = front;
    printf("Queue elements: ");

    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }

    printf("\n");
}

// Main function

int main() {
    
    enqueue(10);
    enqueue(20);
    enqueue(30);

    display();

    dequeue();
    dequeue();

    display();

    return 0;
}


---

How to Compile and Run

Using GCC

1. Save the file as queue_linkedlist.c
2. Open terminal or command prompt
3. Compile the program:


gcc queue_linkedlist.c -o queue_linkedlist


4. Run the executable:


./queue_linkedlist


(On Windows, use queue_linkedlist.exe)

---

Sample Output


Inserted: 10
Inserted: 20
Inserted: 30
Queue elements: 10 20 30
Deleted: 10
Deleted: 20
Queue elements: 30


---

Concepts Covered

* Queue Data Structure
* Linked List implementation
* Dynamic memory allocation (malloc)
* Memory deallocation (free)
* FIFO (First In, First Out) principle
* Pointer manipulation

---

How Queue Works (Linked List Version)

* enqueue() inserts elements at the *rear*
* dequeue() removes elements from the *front*
* front points to the first element
* rear points to the last element
* When the queue becomes empty, both front and rear are set to NULL

This implementation avoids the fixed-size limitation of array-based queues.

---

Time Complexity

* *Enqueue:* O(1)
* *Dequeue:* O(1)
* *Display:* O(n)

---

Advantages Over Array Queue

* No fixed size limit
* Efficient memory usage
* No wasted space
* Dynamic growth

---

⚠️ Recommended Improvements

* Add a *peek()* operation
* Make it *menu-driven*
* Free remaining nodes before program termination
* Add user input functionality

---
