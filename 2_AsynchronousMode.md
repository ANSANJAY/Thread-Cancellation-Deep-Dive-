# Thread Cancellation: Asynchronous vs Deferred 🧵❌

## Table of Contents 📝

1. [Introduction](#introduction-)
2. [Asynchronous Cancellation](#asynchronous-cancellation-)
3. [Deferred Cancellation](#deferred-cancellation-)
4. [Interview Questions](#interview-questions-)

---

## Introduction 📚

- Thread Cancellation is an essential part of multi-threaded programming.
- There are two primary types of thread cancellation: **Asynchronous Cancellation** and **Deferred Cancellation**.
- Understanding both is crucial for effective thread management.

---

## Asynchronous Cancellation 🔄

### What is it? 🤔
- In Asynchronous Cancellation, a cancellation request is sent to the target thread. 
- The operating system queues this request internally.
- It is **not guaranteed** that the thread will be canceled instantly.

### How it Works 🛠️
1. **Thread T1 wants to cancel Thread T2**: While executing at point P1, Thread T1 sends a cancellation request to Thread T2.
2. **Request Queued**: The OS queues this request but doesn't cancel Thread T2 instantly.
3. **Looking for Opportunity**: The OS looks for an appropriate time to cancel Thread T2.
4. **Cancellation**: At time `t = delta T`, the OS finally cancels Thread T2 while it was at point P3 in its execution flow.
5. **Uncertainty**: The exact timing of cancellation is uncertain, making it "asynchronous".

### API 📚
- `pthread_cancel` is commonly used for thread cancellation.

---

## Deferred Cancellation ⏳

### What is it? 🤔
- Introduced to address the drawbacks of Asynchronous Cancellation.
- More details will be covered later.

---

## Interview Questions 📚

### Q1: What are the two main types of Thread Cancellation? 🤔
#### Answer:
The two main types of Thread Cancellation are Asynchronous Cancellation and Deferred Cancellation.

### Q2: What happens when a thread sends a cancellation request in Asynchronous Cancellation? 🔄
#### Answer:
In Asynchronous Cancellation, the cancellation request is queued by the operating system but is not delivered instantly. The OS looks for an appropriate time to cancel the target thread.

### Q3: Is it guaranteed that a thread will be canceled instantly in Asynchronous Cancellation? 🛑
#### Answer:
No, it is not guaranteed. The cancellation request is queued, and the OS looks for an opportunity to cancel the thread, which may not be immediate.

### Q4: What is the role of the operating system in Asynchronous Cancellation? 🖥️
#### Answer:
The operating system queues the cancellation request and looks for an appropriate opportunity to deliver this cancellation signal to the target thread. The exact timing is not guaranteed.

---

