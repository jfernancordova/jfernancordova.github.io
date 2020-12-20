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

#### An API must be designed from its consumer’s perspective and not its provider’s

* Who are the users?
* What can they do?
* How do they do it?
* What do they need to do it?
* What do they get in return?
* Where do the inputs come from?
* How are the outputs used?

---

#### How can I visualize these questions in a friendly way?
* API goals canvas.
* Use Cases.

---

#### Basic principles
* Goals mean resources and actions pairs.
* A REST API represents its goals with actions (HTTP methods) on resources (paths | user-friendly).
* Resources' adopted format is /{plural collection’s name}/{item id}.
* The aim of the REST architectural style is to facilitate building distributed systems that are efficient, scalable, and reliable.

#### HTTP Methods
* PATCH can be used to update a resource (request’s body).
* PUT can be used to replace an existing resource or to create a nonexisting one (the created resource should be returned).
* POST can be used to create a nonexisting resource in the request’s body (it does not return information).

#### Constraints for APIs RESTful
* Client/server separation (consumers/providers)
* Statelessness
* Cacheability
* Layered systems
* Code on demand (A server can transfer executable code to the client)
* Uniform interface (the concept of identified resources)

#### The OpenAPI Specifcation (OAS)




