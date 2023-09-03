# Implementing Deferred Cancellation in C Code 🛠️👨‍💻

## Overview 📚

In this lecture, the following key topics are discussed:

1. Implementing deferred cancellation in an existing code file.
2. Addressing the problem of invariants.
3. Specific code changes and the usage of different APIs.
4. Ensuring thread cancellation safety.

## Implementing Deferred Cancellation 🔨

### Steps 📋

1. Rename the last edited file to `deferred_cancellation.c`.
2. Open the file and proceed with the code changes.

### Problems Addressed 🤔

- With clean-up handlers, we had already addressed the problem of resource leaking.
- However, the thread was still prone to the problem of invariants.

## Problem of Invariants 🚫

### Definition 📝

- Invariants are conditions that must hold true during the execution of a program or thread.

### Risks 🚨

- Invoking functions like `printf` or system calls like `fwrite` can lead to undefined behavior if the thread is canceled asynchronously.

### Why It's an Issue 🤷‍♂️

- Cancellation during a system call could corrupt the kernel.
  
## Making Code Changes 🛠

### Switching to Deferred Cancellation 👇

- Use `pthread_cancel_deferred` to switch the thread's cancellation mode to deferred.

### Inserting Cancellation Points 📌

- Add a call to `pthread_test_cancel` at line number 78.
  
### Final Implementation 🌟

- The thread will now only cancel at line 78, ensuring that it won't interrupt the execution of other functions and system calls.
  
---

## Interview Questions and Answers ❓💡

### Q1: How do you implement deferred cancellation in existing code?

🅰️ To implement deferred cancellation in existing code, you rename the code file to `deferred_cancellation.c` and insert the `pthread_cancel_deferred` API to switch the cancellation mode. Additionally, you define cancellation points using the `pthread_test_cancel` API.

### Q2: What is the problem of invariants and why is it significant?

🅰️ The problem of invariants arises when conditions that should hold true during the execution of a program are disrupted. It's significant because it can lead to undefined behavior and potentially corrupt the kernel if the thread is canceled during a system call.

### Q3: How does deferred cancellation help in making a function thread cancellation safe?

🅰️ Deferred cancellation allows you to specify where a thread can be canceled, thus ensuring that a function's internal logic is not abruptly terminated. This makes the function thread cancellation safe.

### Q4: What are the risks of asynchronous cancellation?

🅰️ Asynchronous cancellation can lead to undefined behavior, corruption of the kernel, and failure to maintain invariants because the thread can be canceled at any point during its execution.

### Q5: Where would you typically insert a cancellation point in a program that uses deferred cancellation?

🅰️ A cancellation point should be inserted at a position where it's safe for the thread to be canceled without causing issues such as resource leaks or corruption. In the given example, the cancellation point is inserted at line 78 using `pthread_test_cancel`.

### Q6: What is `pthread_test_cancel` and how does it work?

🅰️ `pthread_test_cancel` is an API that checks if there are any pending cancellation requests for the thread. If there are, the thread will be canceled at that point.

---

This comprehensive set of notes and interview questions should provide you with a thorough understanding of implementing deferred cancellation in threads and how to make your thread functions safe from cancellation-related issues. 📘✅
