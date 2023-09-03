# Deferred Cancellation in Threads in C 🛑👨‍💻

## Overview 📚

In this session, the following key points are discussed:

1. Introduction to deferred cancellation in threads.
2. How deferred cancellation is different from asynchronous cancellation.
3. The concept of cancellation points.
4. Developer's role in controlling the cancellation points.

## Understanding Deferred Cancellation 🤔

### Definition 📝

- Deferred cancellation allows the programmer to control the points at which a thread can be canceled during its execution.

### Comparison with Asynchronous Cancellation 🔄

- In asynchronous cancellation, the thread can be canceled at any point, whereas deferred cancellation gives the developer control over when a thread can be canceled.

### Application 🛠

- Useful for handling problems like invariants that cannot be handled by asynchronous cancellation.

## Cancellation Points 📍

### Definition 📝

- Specific points in a thread's execution flow where it can be canceled are called 'cancellation points'.

### Developer Control 🔧

- Developers can specify cancellation points using the API `thread_test_cancel`.

### Example 🧩

- For thread T1, point P4 could be a cancellation point. A pending cancellation signal will only cancel the thread when it reaches a cancellation point.

## Best Practices 🏆

- Choose cancellation points wisely to avoid issues like resource leaking or deadlocks.
  
---

## Interview Questions and Answers ❓💡

### Q1: What is deferred cancellation and how is it different from asynchronous cancellation?

🅰️ Deferred cancellation allows a programmer to specify which points in a thread's execution flow are eligible for cancellation. In asynchronous cancellation, a thread can be canceled at any point without developer control.

### Q2: What is a cancellation point?

🅰️ A cancellation point is a specific location in a thread's execution where the thread is allowed to be canceled. It is specified by the developer using `thread_test_cancel`.

### Q3: Why would a developer prefer deferred cancellation over asynchronous cancellation?

🅰️ Deferred cancellation allows the developer to control when a thread can be canceled, making it easier to manage problems like invariants, resource leaks, or deadlocks.

### Q4: How do you define a cancellation point in a thread?

🅰️ A cancellation point in a thread is defined by invoking the API `thread_test_cancel` at the specific point in the thread's code.

### Q5: What are the risks involved in choosing cancellation points?

🅰️ The risks include potential resource leaks, deadlocks, and problems with invariants if cancellation points are not chosen wisely.

### Q6: Can you describe how a thread behaves when a cancellation signal is pending and it reaches a cancellation point?

🅰️ When a thread with a pending cancellation signal reaches a cancellation point, the thread will be terminated at that specific point as designated by the developer.

### Q7: Whose responsibility is it to decide the cancellation points?

🅰️ It is the programmer's or developer's responsibility to choose the cancellation points.

---

This set of notes and interview questions should provide you with a deep understanding of deferred cancellation in threads, including how to implement it and the considerations involved. 📘✅
