

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

