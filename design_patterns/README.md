# Introduction to Design Patterns with Python

- Novice
- By: Javier Valenzani
- Weight: 1
- Your score will be updated as you progress.

## Concepts

For this project, we expect you to look at these concepts:

- Introduction to Design Patterns with Python - Conceptual Companion
- [Design Patterns](https://intranet.hbtn.io/concepts/1527)

## Introduction and Context

Writing classes is only one part of object-oriented programming. A more difficult step is deciding how responsibilities should be distributed between objects so that a program remains understandable, maintainable, and easy to extend.

Several design problems appear repeatedly in software systems:

- How should objects be created without scattering construction logic across the codebase?
- How can one part of the system react to changes in another without becoming tightly coupled to it?
- How can behavior be extended without modifying existing code or creating an unmanageable number of subclasses?

These problems appear in real applications such as notification systems, APIs, payment platforms, user interfaces, and content management tools. Solving them well requires more than syntax. It requires good design decisions.

A design pattern is a reusable way of organizing code to solve a recurring design problem. A pattern is not a finished implementation to copy mechanically. Instead, it describes a structure of responsibilities and interactions that has proven useful in many systems.

A design pattern usually helps answer three questions:

- What design problem is being solved?
- Which roles do the participating classes or objects play?
- Why does this structure make the system easier to change?

In this project, you will work with three foundational patterns from the Gang of Four catalog. Each belongs to one major category:

- Creational patterns focus on how objects are created
- Behavioral patterns focus on how objects communicate
- Structural patterns focus on how objects are composed

The goal of this project is not to memorize patterns by name. The goal is to understand why a given structure solves a specific problem, and how that structure supports maintainable object-oriented design.

### Important Note About Python

Design patterns were originally described in a language-agnostic way, but the way they are expressed depends on the programming language.

In Python, some patterns may look simpler or more flexible than in statically typed languages. Features such as dynamic typing, first-class objects, and composition can reduce the amount of boilerplate needed.

For that reason, this project does not expect rigid textbook implementations. Instead, it focuses on the design problem behind each pattern and on the reasoning that makes the solution useful.

## Skills Developed

By completing this project, you will develop the ability to:

- Identify when code becomes difficult to extend because responsibilities are too tightly coupled
- Recognize recurring design problems in object-oriented systems
- Extend existing systems without modifying their core logic
- Reason about maintainability and flexibility, not only correctness
- Explain why a particular structure improves the design of a program

## Learning Objectives

After completing this project, you should be able to:

**Understand what design patterns are**

- Distinguish between creational, behavioral, and structural patterns
- Explain what kind of problem each pattern solves
- Describe patterns as reusable design strategies rather than code templates

**Apply the Factory pattern**

- Identify the coupling caused by scattered direct instantiation
- Extend a factory registry to support a new type without modifying the core creation logic

**Apply the Observer pattern**

- Explain how a subject can publish events without knowing the concrete type of every listener
- Add a new observer and configure it to receive only specific topics

**Apply the Decorator pattern**

- Explain why composition can avoid subclass explosion
- Add a new decorator that composes correctly with existing ones without modifying any existing class

## Core Concepts

Before starting the tasks, keep these ideas in mind:

- Creational patterns focus on object creation
- Behavioral patterns focus on communication between objects
- Structural patterns focus on composition and arrangement of objects

Two important design ideas appear throughout the project:

- **Open/Closed Principle**: code should be open for extension, but closed for modification
- **Composition over inheritance**: behavior can often be extended more flexibly by combining objects rather than creating many subclasses

These ideas are closely related to broader object-oriented design principles such as SOLID, which aim to make software easier to maintain and evolve.

## Resources

### Required

- [Refactoring Guru — Design Patterns Introduction](https://refactoring.guru/design-patterns)
- [Refactoring Guru — Factory Method](https://refactoring.guru/design-patterns/factory-method)
- [Refactoring Guru — Observer](https://refactoring.guru/design-patterns/observer)
- [Refactoring Guru — Decorator](https://refactoring.guru/design-patterns/decorator)

### Complementary Concepts

- [Geeks for Geeks — SOLID Principles with Real Life Examples](https://www.geeksforgeeks.org/system-design/solid-principle-in-programming-understand-with-real-life-examples/)
- [Open/Closed Principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle)
- [Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance)
- [Conceptual companion for this project](https://intranet.hbtn.io/concepts/1527)

### Recommended Python References

- [Python typing.Protocol](https://docs.python.org/3/library/typing.html#typing.Protocol)
- [Python abc.ABC and abstractmethod](https://docs.python.org/3/library/abc.html)

## AI Tools

Any LLM-based assistant is allowed.

Use AI to explore ideas, compare alternatives, or clarify terminology. Do not use it as a substitute for understanding. If you cannot explain why a pattern helps in a given situation, your understanding is still incomplete.

## General Requirements

- Python 3.10 or later
- Every submitted file must start with:

```
#!/usr/bin/env python3
```

- Code must follow PEP 8
- No external dependencies are required unless explicitly stated
- Files must run with:

```
python3 <filename>
```

## Final Note

Completing the TODOs is only one part of the work. By the end of this project, you should be able to explain:

- what problem each pattern solves,
- why the structure is organized the way it is,
- and how that structure makes future changes easier and safer.