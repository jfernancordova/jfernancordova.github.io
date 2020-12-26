---
layout: post
title: My Object-Oriented Programming Style
tags:
  - 3 min read
---

## Introduction
---

I’ve used OOP since I started coding and it was hard for me to understand how OOP code can model reality through objects. I think it’s a good idea to know the fundamentals before starting to code using OOP, since some terms can result confusing, for example, abstractions, interfaces, or polymorphism.

Practicing on projects from scratch can be a good entry point, but the truth is that when you start to code with other people, do refactors, and think if it exists a good way to implement new things, I realized it’s not easy, and I felt how frustrated it is.

Thanks to [Matthias Noback’s object design style](https://livebook.manning.com/book/object-design-style-guide/about-this-book/) and some notes from [Object-Oriented Analysis and Design with Applications](https://www.amazon.com/Object-Oriented-Analysis-Design-Applications-3rd/dp/020189551X), books that I highly recommend, I could understand how OOP could be a great solution, especially for scalable Apps or APIs Restful.

---

## Semantics
---
I always create interfaces or classes with minor responsibilities and try to name them with a meaningful name. It can be very tedious and risky, no matter encapsulations, inheritances, or associations.
I define a class or interface in a singular noun, attributes or properties too, obviously if I know the attribute's type, for example, an array, it would be a plural noun, the methods are verbs, as a prefix (get, process, have) or any word that has an action to do, it can be a plural or singular noun, it always depends about the business model, that's why semantic is very important.

---

## Comments and Simplicity
---
I don't comment any class, interface, methods, or attributes. If the object has a meaningful name, the comments would be unnecessary. It exists situations where an object could be hard to read, I prefer to document it instead declare comments. I follow the [Visual Debt](https://laracasts.com/series/php-bits/episodes/1) and [Simple Rules for Simpler Code](https://laracasts.com/series/simple-rules-for-simpler-code) by Jeffrey Way. He explains the code simplicity in a practice way!

---

## More Best Practice and Less Code Smell 
---
For me, experience is essential at all. I have learned a lot from the Code Review, and  I can say that it's the best way to understand the different perspectives of other developers.
I always try to follow these rules/principles when I start coding
* [Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance)
* [Tell Don't Ask](https://martinfowler.com/bliki/TellDontAsk.html)
* [Law Of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter)
* [Avoid Anemic domain objects](https://www.martinfowler.com/bliki/AnemicDomainModel.html) (anti-pattern)
* [SOLID](https://dev.to/trekhleb/s-o-l-i-d-principles-around-you-1o17)
* [Avoid Big Ball of Mud](https://thedomaindrivendesign.io/big-ball-of-mud/)
* [Avoid Train Wreck](https://wiki.c2.com/?TrainWreck) (anti-pattern)
* [Rule of thumb ](https://en.wikipedia.org/wiki/Rule_of_thumb)
* [Command (write) – Query (read) separation (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html)
* [Kent Beck's four rules of Simple Design](https://martinfowler.com/bliki/BeckDesignRules.html)
* Replace primitives with objects.
* Value objects and DTOs are wrappers for primitive-type values.
* Value objects are immutables and give meaning and useful behavior.
* Services are immutables and Entities are mutables.
* Mark methods and properties private by default.

There are a lot of principles or rules to design well code and avoid code smells. The secret for me, it's simplicity, I know that it's not easy, but the practice, it becomes easier.

---

## Design Patterns
---
I prefer to implement them when I don't have alternative because I've made a lot of mistakes thinking that design patterns are the solution for everything.

Design Pattern can be a solution for complex features, frameworks, or scalable APIs. The code can be more cohesive, reusable, and understandable, so, before implementing one, I ask myself:

* Do I need to have a polymorphic behavior? I consider creating a simple interface.
* Do I need extra reusable behavior and different abstractions? I think implementing an abstract class. 
* Do I need more validations and accessibility? I create value objects or DTOs (primitive-type values).
* Do I need external or own independent functionalities? I create immutable services and apply Dependency Injection.
* Do I need multiple instances with reusable behavior? I apply a simple factory.
* If a simple factory doesn't work because of complexity, then I apply the Factory Method.
* Don't I need multiple instances? I read what is the most convenient design pattern for my feature or implementation.