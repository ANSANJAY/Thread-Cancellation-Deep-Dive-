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


