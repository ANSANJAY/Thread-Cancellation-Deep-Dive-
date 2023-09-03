# Thread Cancellation and Problem of Invariants 🧵🛑

## Overview 📑

This document discusses the complex topics of thread cancellation and the resulting problem of invariants in a multi-threaded programming environment. We will be focusing on:

1. How to cancel threads in a system.
2. The implications of abrupt thread cancellation.
3. Real-world scenarios where thread cancellation may lead to data corruption and other issues.
   
## Thread Cancellation in POSIX 🛠

### Implementation 🖥

- File named `async_cancellation.c` contains the solution for thread cancellation.
- The file initially had a master-slave implementation.
- The file focuses on implementing **asynchronous** thread cancellation.

### Code Structure 🏗

- **Left-hand side**: A `while(1)` loop to interact with the user.
- **Right-hand side**: A function that acts as a thread function for all the slave threads.

### Canceling a Thread ❌

1. When the user chooses an option to cancel a thread, the program asks for the thread ID.
2. POSIX API provides `pthread_cancel(thread_handle)` to cancel a specific thread.
3. Threads must be **cancelable** for the `pthread_cancel` to work.
4. Use `pthread_setcancelstate(PTHREAD_CANCEL_ENABLE, NULL)` to make a thread cancelable.

### Modes of Cancellation 🔄

- Deferred Cancellation
- Asynchronous Cancellation
- Use `pthread_setcanceltype(PTHREAD_CANCEL_ASYNCHRONOUS, NULL)` to set cancellation type.

---

## Problem of Invariants ⚠️

### What Are Invariants? 🤔

- Invariant refers to a data structure in an **inconsistent state**.
- Invariants occur when a thread is canceled abruptly during a critical operation.

### Example: Doubly Linked List 🖇

- Consider a doubly linked list with four nodes.
- A thread is set to remove one of the middle nodes.
- If the thread is canceled after partially updating the pointers, the data structure becomes **inconsistent**.

### Other Examples 🌳🖥

- Balanced trees like Red-Black and AVL trees
- System calls, which may even corrupt the kernel if a thread is canceled mid-way.

### Rule of Thumb 👍

- Do not allow threads to get canceled while updating a data structure.

---

## Interview Questions and Answers 🤝

### Q1: How do you make a thread cancelable in POSIX?

🅰️ To make a thread cancelable in POSIX, you use the API `pthread_setcancelstate(PTHREAD_CANCEL_ENABLE, NULL)`.

### Q2: What are invariants in the context of thread programming?

🅰️ Invariants refer to data structures in an inconsistent state, often caused by abrupt cancellation of threads during critical operations.

### Q3: What could be the consequences of invariants?

🅰️ Consequences include data corruption, memory leaks, and even deadlocks.

### Q4: Can one thread mark another thread as cancelable or non-cancelable?

🅰️ No, one thread cannot change the cancelability behavior of another thread in the process.

### Q5: What are the risks of asynchronous thread cancellation?

🅰️ Asynchronous cancellation can result in resource leaks, invariants, and even deadlocks.

---

By understanding these concepts and the risks involved, you'll be better prepared to manage threads in your programs. 🧠💡
