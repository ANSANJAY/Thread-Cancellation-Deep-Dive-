

# Thread Cancellation Example Program 🛠️

## Table of Contents 📝

1. [Introduction](#introduction-)
2. [Program Overview](#program-overview-)
3. [User Interaction](#user-interaction-)
4. [Implementation Details](#implementation-details-)
5. [Interview Questions](#interview-questions-)

---

## Introduction 📚

This document describes an example program stored in `Multithreading Bible/thread basics/thread cancellation/master_slave1.c`. The program demonstrates thread cancellation by creating multiple threads that write to files.

---

## Program Overview 🖥️

- The program creates **5 threads**.
- Each thread writes a string into a file named `threadX.txt`, where `X` is the thread ID.
- Thread IDs are integers ranging from 0 to 4.

### File Writing Logic 📝

Each thread writes the following string to its respective file:

```plaintext
"I am thread [thread_id]"
```

---

## User Interaction 🤝

- When the program runs, it shows a menu with only one choice: **"Cancel the thread."**
- The user must enter a thread ID to cancel the corresponding thread.

### Thread Cancellation 🛑

Thread cancellation is triggered based on the user-provided thread ID.

---

## Implementation Details 🛠️

- The macro `n_slaves` is set to 5, determining the number of threads.
- A global array holds the thread handles.
- Each thread runs an infinite loop with a `sleep(1)` call, continuously writing to its text file.
  
### Code Snippets 📜

To generate the filename, the program uses the `sprintf` function:

```c
// Derive the filename using the thread ID
sprintf(filename, "thread%d.txt", thread_id);
```
## Interview Questions 📚

### Q1: What does the example program in `master_slave1.c` demonstrate? 🤔
#### Answer:
The example program demonstrates thread cancellation by creating 5 threads that write to individual files. It offers an option to the user to cancel a thread based on its ID.

### Q2: How does the program determine which thread to cancel? 🧐
#### Answer:
The program displays a menu that prompts the user to enter a thread ID. The entered ID is used to cancel the corresponding thread.

### Q3: How does each thread determine the name of the file it writes to? 📝
#### Answer:
Each thread uses its thread ID to create a file named `threadX.txt`, where `X` is the thread ID. It uses `sprintf` to format the filename.

### Q4: What string is written by each thread to its respective file? ✏️
#### Answer:
Each thread writes the string "I am thread [thread_id]" to its respective file.

### Q5: How are the thread handles stored and accessed in the program? 📋
#### Answer:
The thread handles are stored in a global array, allowing easy access for operations like cancellation.

# Asynchronous Thread Cancellation in C 🚨

## Table of Contents 📝
1. [Introduction](#introduction-)
2. [Making Threads Cancelable](#making-threads-cancelable-)
3. [Thread Cancellation API](#thread-cancellation-api-)
4. [Demo Execution](#demo-execution-)
5. [Interview Questions](#interview-questions-)

---

## Introduction 📚
- This section discusses implementing thread cancellation in a C file named `async_cancellation.c`.
- We rename the Master-Slave 1.0C program to this name after implementing thread cancellation.

---

## Making Threads Cancelable 👷
- By default, threads are not cancelable.
- To make a thread cancelable, use the POSIX API `pthread_set_cancel_state`.
- Two constants are used:
  1. `PTHREAD_CANCEL_ENABLE` for making a thread cancelable.
  2. `PTHREAD_CANCEL_DISABLE` for making a thread non-cancelable.
- Threads can dynamically change this state during execution.

---

## Thread Cancellation API 🛠️
- `pthread_cancel` API is used to cancel a thread.
- The handle of the thread to be canceled is passed as an argument.
- The thread must be cancelable for this API to take effect.
- The cancellation mode needs to be set using `pthread_set_cancel_type`, either to deferred or asynchronous mode.
- Note: These APIs only affect the calling thread, as they don't take a thread handle as an argument.

---

## Demo Execution 🏃‍♂️
- The program has a UI loop that interacts with the user.
- Users can select which thread to cancel by specifying its ID.
- When a thread is canceled, its corresponding write-to-file operation stops.
- Once a thread is canceled, it can't be resumed; a new thread must be created from scratch.

---

## Interview Questions 📚

### Q1: What is the purpose of `pthread_set_cancel_state` API? 🤔
#### Answer:
It is used to specify whether a thread is cancelable (`PTHREAD_CANCEL_ENABLE`) or non-cancelable (`PTHREAD_CANCEL_DISABLE`).

### Q2: What does the `pthread_cancel` API do? 🛠️
#### Answer:
It is used to cancel a thread. The thread handle of the thread to be canceled is passed as an argument.

### Q3: How do you specify the mode of thread cancellation? 🛑
#### Answer:
The mode is set using the `pthread_set_cancel_type` API. It can either be set to deferred or asynchronous cancellation.

### Q4: Can one thread change the cancelability behavior of another thread? 👨‍💻
#### Answer:
No, one thread cannot change the cancelability behavior of another thread because the APIs `pthread_set_cancel_state` and `pthread_set_cancel_type` only affect the calling thread.

### Q5: What happens when you cancel a thread? ⚠️
#### Answer:
When a thread is canceled, its execution is stopped. If it was performing a write-to-file operation, that operation would stop, and the thread can't be resumed.



