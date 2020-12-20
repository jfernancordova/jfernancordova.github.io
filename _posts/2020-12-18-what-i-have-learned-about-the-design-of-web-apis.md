---
layout: post
title: What I've learned about the design of web APIs
tags:
 - 3 min read
---

## Introduction
---

As a Backend Developer, I realized the design of a web API is the most important, so thanks to [Phil Sturgeon's book](https://apisyouwonthate.com/books/build-apis-you-wont-hate) and [Arnaud Lauret's book](https://www.manning.com/books/the-design-of-web-apis), I could learn incredible concepts which they can be useful at the moment of creating an API efficiently!

## Fundamentals
---

An API must be designed from its consumer’s perspective and not its provider’s

* Who are the users?
* What can they do?
* How do they do it?
* What do they need to do it?
* What do they get in return?
* Where do the inputs come from?
* How are the outputs used?

How can I visualize these questions in a friendly way?

* API goals canvas
* Uses Cases
* Sequences Diagrams

### Basic principles

* Goals mean resources and actions pairs. 
* Resources are represented by paths, and actions are represented by HTTP methods.
* A REST API represents its goals through actions on resources.
* 

