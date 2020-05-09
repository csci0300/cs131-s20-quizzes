CS 131 Final Quiz 2020
======================

Please place all the answers for your quiz in this file.
Please do not place your name anywhere in this file.

Multiple Choice Questions
-------------------------

Question 1:

Question 2:

Question 3:

Question 4:

Question 5:

Question 6:

Question 7:

Question 8:

Question 9:

Question 10:

Question 11:

Question 12:

Question 13:

Question 14:


Short Response Questions
------------------------

Question 15:
------------
 1.
 2.
 3.
 4.
 5.
 6.

Question 16:
------------
 * arg1:
 * arg2:
 * arg3:

Question 17:
------------
 1.
 2.
 3.

Question 18:
------------
 1.
 2.
 3.

Question 19:
------------
 format: address: bytes
* 0x7fffffffe408:
* 0x7fffffffe400:
* 0x7fffffffe3f8:
* 0x7fffffffe3f0:
* 0x7fffffffe3e8:
* 0x7fffffffe3e0:
* 0x7fffffffe3d8:
* 0x7fffffffe3d0:
* 0x7fffffffe3c8:

Question 20:
------------
 1.
 2.

Question 21:
------------
 Answer:

Question 22:
------------
 Answer:

Question 23:
------------
 Answer:


Long Response Questions
------------------------

Question 24:
------------
 Answer:

Question 25:
------------
```cpp
void* malloc_wrapper(size_t size) {
  // <your code here>
}
```

Question 26:
------------
 Answer:

Question 27:
------------
a.
```shell
$ <your code here>
```
b.
```cpp
// <your code here>
```

Question 28:
------------
 Answer:

Question 29:
------------
a.
```cpp
// <modify the following code>
// list node struct
typedef struct list_node {
    int value;              // value of the node
    struct list_node* next; // pointer to the next node
    std::mutex mtx;         // mutex for this node
} list_node_t;

// list struct
typedef struct list {
    list_node_t* head; // head node of the list
} list_t;


/**
 * Appends the given value to the end of the list.
 * Returns nothing.
 */
void append(list_t* list, int value) {
    // create a new node
    list_node_t* new_node = new list_node_t();
    new_node->next = NULL;
    new_node->value = value;

    // if the list is empty, set the head to new node
    if (list->head == NULL) {
        list->head = new_node;
        return;
    }

    // list is not empty; iterate to the end and append new node
    list_node_t* current = list->head;
    current->mtx.lock();
    while (current->next != NULL) {
        current->mtx.unlock();
        current = current->next;
        current->mtx.lock();
    }
    current->next = new_node;
    current->mtx.unlock();
}

/**
 * Searches the list for the target value.
 * Returns true if found; false otherwise.
 */
bool search(list_t* list, int value) {
    // list is empty
    if (list->head == NULL) {
        return false;
    }

    list_node_t* current = list->head;

    // iterate through the list
    current->mtx.lock();
    while (current->next != NULL) {
        current->mtx.unlock();
        // found the first instance of value
        if (current->value == value) {
            return true;
        }
        current = current->next;
        current->mtx.lock();
    }

    // we didn't find the value
    current->mtx.unlock();
    return false;
}
```
b. Answer:

Question 30:
------------
 Answer:


CS 131 Feedback
---------------

Question 31:
------------
 Answer:

Question 32:
------------
 Answer:

Question 33:
------------
 Answer:
