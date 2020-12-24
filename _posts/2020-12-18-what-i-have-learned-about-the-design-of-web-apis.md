---
layout: post
title: What I've learned about the design of web APIs
tags:
 - 3 min read
---

## Introduction
---

I realized the design of a web API is the most important, so thanks to [Phil Sturgeon's book](https://apisyouwonthate.com/books/build-apis-you-wont-hate) and [Arnaud Lauret's book](https://www.manning.com/books/the-design-of-web-apis), I could learn specific concepts in which are useful at the moment of creating an API efficiently and easy to use!

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
* [Use Cases](https://en.wikipedia.org/wiki/Use_case)
* [UML diagrams](https://www.uml-diagrams.org/)

---

#### Basic principles
* Goals mean resources (user-friendly) and actions pairs.
* A REST API represents its goals with actions (HTTP methods) on resources (paths).
* Resources' adopted format is /{plural collection’s name}/{item id}.
* The aim of the REST architectural style is to facilitate building distributed systems that are efficient, scalable, and reliable.
* Choosing the right granularity for the goals.
* Extensibility is a software engineering and systems design principle where the implementation takes future growth into consideration.
* An API evolution must be carefully designed in order to avoid breaking changes.
* APIs have to be reviewed (validated, analyzed, scrutinized, checked, tested, and so on).

---

#### HTTP Methods
* PATCH can be used to update a resource (request’s body).
* PUT can be used to replace an existing resource or to create a nonexisting one (the created resource should be returned).
* POST can be used to create a nonexisting resource in the request’s body (it does not return information).
* DELETE can be used on a resource to delete, undo, or cancel the concept represented by a URL.

---

#### Constraints for APIs RESTful
* Client/server separation (consumers/providers)
* Statelessness
* Cacheability
* Layered systems
* Code on demand (A server can transfer executable code to the client)
* Uniform interface (the concept of identified resources)

---

#### API description formats
It is a data format whose purpose is to describe an API.
* [The OpenAPI Specification (OAS) + Swagger Specification](https://swagger.io/specification/)
* [JSON Schema specification](https://json-schema.org/specification.html)
* [JSON:API](https://jsonapi.org/)

---

#### Data serialization format
* [YAML (human-friendly)](https://yaml.org/)
* [JSON](https://www.json.org/json-en.html)
* [XML](https://www.xml.com/)

---

#### Simple Rules
* Ensure that each goal provides a straightforward interaction.
* Ensure that outputs and inputs are consistent between goal calls.
* When possible, prevent errors by adding data to existing goals to create new goals.
* Any representation must be easily understandable by people and programs.
* Any representation must be as informative as possible.
* Error feedback must provide enough elements to understand and maybe fx the problem.
* The API designer is responsible for determining what data should be cached and for how long.
* Network communication efficiency can be a major concern.
* Optimizing communication for efficiency can have important effects on the design.
* API designer must question, challenge, investigate, validate, and analyze everything regarding the design.

---

#### Considerations
* Designing APIs requires us to fully observe the context in which these will be consumed and provided in order to ensure that these fulfill all consumers' needs in the best possible way.
* Designing APIs requires us to be aware of the consumers' contexts, including their network environments, habits, and limitations.
* Designing APIs requires us to carefully consider the provider’s limitations, and to solve problems without impacting the design (if possible) and adapting the design (if not).
* Designing APIs requires us to ignore fashion and personal preferences. Just because you like or know a certain tool/design/practice doesn’t mean that it will be the ideal solution for all API design matters.

---

#### Consistency
* Great way of being predictable within an API.
* Across an organization/company/team’s APIs.
* With the domain(s) of an API.
* With the rest of the world.
* With rules in a document called the “API Design Guidelines” or “API Design Style Guide.”
* With appropriate level of granularity for versioning.

---

#### Documentation
The best-known API documentation is the reference documentation that describes the interface contract of the API. It lists the available goals and describes their inputs and outputs.
The API lifecycle Growing APIs requires that we know the API lifecycle and understand that it runs in parallel with others.
* [ReDoc](https://redocly.github.io/redoc/)
* [PlantUML](https://plantuml.com/)

---

#### Web Concepts
Designing APIs and building API design guidelines requires a solid understanding of web concepts like HTTP headers and status codes.
* [Web Concepts website](http://webconcepts.info/)
* [The API Stylebook](http://apistylebook.com)

---

## API Styles
---
* [REST or Restful - Architecture Style](https://restfulapi.net/)
* [gRPC - Open Source remote procedure call and exposes functions](https://grpc.io/docs/languages/csharp/quickstart/)
* [GraphQL - Allowing consumers to retrieve exactly the data they want](https://graphql.org/)


