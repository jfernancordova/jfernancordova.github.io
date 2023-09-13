---
layout: post
title: Concurrency in Go
tags:
  - 5 min read
---

## Introduction
---
Concurrency is a fundamental aspect of modern software development, and in the world of Go programming, it plays an important role. 
Go, with its goroutines and channels, provides a powerful framework for building concurrent applications. 
In this article, we'll explore the fundamentals,techniques and patterns by delving into the [GitHub repository](https://github.com/jfernancordova/go-concurrency).

<br>

## The repository
---
Before we dive into the specifics, let's take a moment to understand the purpose and contents of the repository:
- it contains go code examples and utilities related to concurrency.
- it covers a range of topics, from basic to more advanced.
- it contains different problems in which are solved using goroutines, mutexes and waitgroups.

<br>

## Key Concepts
---

### Goroutines
These lightweight threads of execution enable us to run concurrent code without the heavy overhead associated with traditional threads. The repository showcases numerous examples of creating and managing goroutines.

### Channels
Channels are Go's way of enabling communication and synchronization between goroutines. They act as conduits through which data can flow. The repository provides practical examples of using channels to coordinate concurrent tasks.

### Synchronization
Concurrency often requires synchronization to prevent race conditions and ensure proper execution order. The repository demonstrates techniques like mutexes and wait groups to coordinate goroutines effectively.

<br>

## Problems solved
---

- [Producer–consumer problem](https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem)
- [Sleeping barber problem](https://en.wikipedia.org/wiki/Sleeping_barber_problem)
- [Dining philosophers problem](https://en.wikipedia.org/wiki/Dining_philosophers_problem)
- [The Account Balance](https://github.com/jfernancordova/go-concurrency/blob/main/mutexes_waitgroups/account_balance/README.md)

<br>

## Conclusion
---

Concurrency is a powerful tool in the Go programming language, and the repository serves as an invaluable resource for anyone looking to master this aspect of Go development. By understanding goroutines, channels, and synchronization techniques.

[Link to the Concurrency in Go Repository](https://github.com/jfernancordova/go-concurrency).

**Happy coding and concurrent programming in Go!**

<br>

## Bibliography
---
- [Working with Concurrency in Go](https://www.udemy.com/course/working-with-concurrency-in-go-golang/)
- [Go in Action](https://www.manning.com/books/go-in-action)