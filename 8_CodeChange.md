# Implementation of Thread Cleanup Handlers in C 🛠️🔍

## Overview 📑

In this lecture, we:

1. Modify an existing C program to handle thread cancellation gracefully using thread cleanup handlers.
2. Address two types of resources: heap memory and open files.
3. Illustrate the use of `pthread_cleanup_push()` and `pthread_cleanup_pop()`.

## Code Structure 🗺️

- **Main Function**: No changes are needed.
- **Thread Function**: This is where we add our cleanup handlers.
  
## Adding Cleanup Handlers 🧹🛠

### Memory Cleanup Handler 🧠

1. Invoke `pthread_cleanup_push()` to add a cleanup function for heap memory.
2. The first argument is the pointer to the cleanup function that frees the memory.
3. The second argument is the pointer to the heap memory to be freed.

### File Cleanup Handler 📂

1. Similarly, another cleanup handler is added for the open file.
2. The handler function will close the file.

### Balancing Push with Pop 🔄

- After installing the cleanup handlers, use `pthread_cleanup_pop()` to remove them before the function returns.

## Example Code Snippets 📜

### Memory Cleanup Handler

```c
pthread_cleanup_push(memory_cleanup_handler, heap_pointer);
```

### File Cleanup Handler

```c
pthread_cleanup_push(file_cleanup_handler, file_pointer);
```

### Pop Cleanup Handlers

```c
pthread_cleanup_pop(0);
pthread_cleanup_pop(0);
```

## Rules and Best Practices 📏

1. The number of `pthread_cleanup_push()` calls should match the number of `pthread_cleanup_pop()` calls.
2. Install a cleanup handler as soon as a resource (like memory or a file) is successfully allocated.

---

## Interview Questions and Answers 🤝

### Q1: What is the purpose of `pthread_cleanup_push` and `pthread_cleanup_pop` in a C program?

🅰️ The `pthread_cleanup_push` API installs a cleanup handler function for a particular resource, like memory or a file. The `pthread_cleanup_pop` API removes the installed cleanup handlers from the stack. These are essential for handling resource leaking during thread cancellations.

### Q2: What kinds of resources are managed in the example code?

🅰️ In the example code, two types of resources are managed: heap memory and an open file.

### Q3: Why do we need to balance out the number of calls to `pthread_cleanup_push` and `pthread_cleanup_pop`?

🅰️ It is crucial to maintain a balanced number of calls to ensure that each installed cleanup handler has a corresponding removal mechanism. This ensures that resources are managed effectively.

### Q4: How do the cleanup handler functions actually clean up the resources?

🅰️ The memory cleanup handler function frees up the heap memory that was allocated, while the file cleanup handler function closes the open file. These actions take place when the thread receives a cancellation signal.

### Q5: What's the developer's role regarding cleanup handlers if the thread runs to completion without cancellation?

🅰️ If the thread runs to completion without cancellation, the developer must explicitly invoke `pthread_cleanup_pop` to remove the installed cleanup handlers, ensuring proper resource management.

---

This implementation guide and the interview Q&A should give you a comprehensive understanding of how to manage resources effectively using thread cleanup handlers in C. 🌟🛠️
