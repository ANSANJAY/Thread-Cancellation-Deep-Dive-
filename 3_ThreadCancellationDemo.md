

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

# Problems with Asynchronous Thread Cancellation 🚨

## Table of Contents 📝
1. [Introduction](#introduction-)
2. [Problems Overview](#problems-overview-)
3. [Resource Leaking](#resource-leaking-)
4. [Memory Leak](#memory-leak-)
5. [Solutions](#solutions-)
6. [Interview Questions](#interview-questions-)

---

## Introduction 📚
This document outlines the issues that can arise from using asynchronous modes of thread cancellation.

---

## Problems Overview 🚫
- Asynchronous cancellation allows a thread to be canceled at any point in its execution.
- This can lead to issues such as:
  1. Resource Leaking
  2. Data Structure Corruption (Termed 'Invariance')
  3. Deadlocks

---

## Resource Leaking 🚰
- In an asynchronous cancellation mode, a thread could be canceled before it releases certain resources like open file descriptors.
- For example, if a thread opens a file and is canceled before closing it, that leads to a resource leak.

---

## Memory Leak 🧠
- If a thread is using heap memory and is canceled before freeing it, this could result in a memory leak.
- An example was shown where thread IDs were stored in heap memory, which weren't freed when the thread was canceled.

---

## Solutions 🛠️
- Resource leaks can be addressed using **Cleanup Handlers**, which give the thread a chance to clean up before it's canceled.
- Data Structure Corruption and Deadlocks are tackled using **Cancellation Points**.

---

## Interview Questions 📚

### Q1: What are the problems with asynchronous mode of thread cancellation? 🤔
#### Answer:
The problems include Resource Leaking, Data Structure Corruption (also known as 'Invariance'), and Deadlocks.

### Q2: What is Resource Leaking, and how can it occur with asynchronous thread cancellation? 🚰
#### Answer:
Resource leaking happens when a thread is canceled before it has the chance to release certain resources like file descriptors. In asynchronous mode, a thread could be canceled at any point, even before it closes an open file, leading to a leak.

### Q3: What is a Memory Leak in the context of asynchronous thread cancellation? 🧠
#### Answer:
A memory leak occurs when heap memory used by a thread isn't freed before the thread is canceled. This can happen because asynchronous cancellation doesn't give the thread an opportunity to perform clean-up activities.

### Q4: What are Cleanup Handlers and how do they help? 🛠️
#### Answer:
Cleanup Handlers give a thread one last chance to clean up resources before it gets canceled. This mechanism helps prevent resource leaks.

### Q5: What are Cancellation Points, and what problems do they solve? 📍
#### Answer:
Cancellation Points are specific points in the code where a thread can safely be canceled without causing issues like resource leaking, data structure corruption, or deadlocks.


