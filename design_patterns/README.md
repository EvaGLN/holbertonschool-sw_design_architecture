<div align="center"><img src="https://github.com/ksyv/holbertonschool-web_front_end/blob/main/baniere_holberton.png"></div>

# Introduction to Design Patterns with Python

## Table of Contents :

  - [0. Factory — Extending a registry](#subparagraph0)
  - [1. Observer - Adding a new subscriber](#subparagraph1)
  - [2. Decorator - Adding a new wrapper](#subparagraph2)
  - [3. Design Patterns Quiz](#subparagraph3)
# Design Patterns

## Introduction and Context

Writing classes is only one part of object-oriented programming. A more difficult step is deciding how responsibilities should be distributed between objects so that a program remains understandable, maintainable, and easy to extend.

Several design problems appear repeatedly in software systems:

- How should objects be created without scattering construction logic across the codebase?
- How can one part of the system react to changes in another without becoming tightly coupled to it?
- How can behavior be extended without modifying existing code or creating an unmanageable number of subclasses?

These problems appear in real applications such as notification systems, APIs, payment platforms, user interfaces, and content management tools. Solving them well requires more than syntax. It requires good design decisions.

A **design pattern** is a reusable way of organizing code to solve a recurring design problem. A pattern is not a finished implementation to copy mechanically. Instead, it describes a structure of responsibilities and interactions that has proven useful in many systems.

A design pattern usually helps answer three questions:

- What design problem is being solved?
- Which roles do the participating classes or objects play?
- Why does this structure make the system easier to change?

In this project, you will work with three foundational patterns from the **Gang of Four** catalog. Each belongs to one major category:

- **Creational** patterns focus on how objects are created
- **Behavioral** patterns focus on how objects communicate
- **Structural** patterns focus on how objects are composed

The goal of this project is not to memorize patterns by name. The goal is to understand **why a given structure solves a specific problem**, and how that structure supports maintainable object-oriented design.

### Important Note About Python

Design patterns were originally described in a language-agnostic way, but the way they are expressed depends on the programming language.

In Python, some patterns may look simpler or more flexible than in statically typed languages. Features such as dynamic typing, first-class objects, and composition can reduce the amount of boilerplate needed.

For that reason, this project does not expect rigid textbook implementations. Instead, it focuses on the design problem behind each pattern and on the reasoning that makes the solution useful.

---

## Skills Developed

By completing this project, you will develop the ability to:

- Identify when code becomes difficult to extend because responsibilities are too tightly coupled
- Recognize recurring design problems in object-oriented systems
- Extend existing systems without modifying their core logic
- Reason about maintainability and flexibility, not only correctness
- Explain why a particular structure improves the design of a program

---

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

---

## Core Concepts

Before starting the tasks, keep these ideas in mind:

- **Creational patterns** focus on object creation
- **Behavioral patterns** focus on communication between objects
- **Structural patterns** focus on composition and arrangement of objects

Two important design ideas appear throughout the project:

- **Open/Closed Principle**: code should be open for extension, but closed for modification
- **Composition over inheritance**: behavior can often be extended more flexibly by combining objects rather than creating many subclasses

These ideas are closely related to broader object-oriented design principles such as **SOLID**, which aim to make software easier to maintain and evolve.

---

## Resources

### Required

- [Refactoring Guru — Design Patterns Introduction](/rltoken/B3DXwL0i6nNaOYtNk2R80Q)
- [Refactoring Guru — Factory Method](/rltoken/7fsCMxzVKEXIIlaopnbovg)
- [Refactoring Guru — Observer](/rltoken/HOUqT9G0vMdP4hDXlngLdQ)
- [Refactoring Guru — Decorator](/rltoken/kc_6HdVuEFgDDV6dgdSsnw)

### Complementary Concepts

- [Geeks for Geeks — SOLID Principles with Real Life Examples](/rltoken/z-ki-yy_Ce5vLbvOLHVKSA)
- [Open/Closed Principle](/rltoken/FkXJpPvQxtTHR9kGL8WQlw)
- [Composition over inheritance](/rltoken/sGHtNJr7GkO_ectfG3bBbA)
- [Conceptual companion for this project](/rltoken/e6Q8NY0JaKexlFy8BA_dqg)

### Recommended Python References

- [Python `typing.Protocol`](/rltoken/0n_-CzH-sfyWR7x8kAUM5w)
- [Python `abc.ABC` and `abstractmethod`](/rltoken/6mMRj1hwpzxbCwPZl_8R9w)

### AI Tools

Any LLM-based assistant is allowed.

Use AI to explore ideas, compare alternatives, or clarify terminology. Do not use it as a substitute for understanding. If you cannot explain why a pattern helps in a given situation, your understanding is still incomplete.

---

## General Requirements

- Python 3.10 or later
- Every submitted file must start with:

```python
#!/usr/bin/env python3
```

- Code must follow **PEP 8**
- No external dependencies are required unless explicitly stated
- Files must run with:

```bash
python3 <filename>
```

---

## Final Note

Completing the TODOs is only one part of the work. By the end of this project, you should be able to explain:

- what problem each pattern solves,
- why the structure is organized the way it is,
- and how that structure makes future changes easier and safer.


## Task
### 0. Factory — Extending a registry <a name='subparagraph0'></a>

#### Design Problem

In many systems, object creation is spread across several parts of the code. This may start as something simple, but it becomes harder to maintain when new concrete types are added.

#### Friendly scenario

Imagine a mobility platform that supports buses, trains, bikes, and scooters. If different parts of the application create these objects directly, adding a new vehicle type requires modifying several places. A factory centralizes that decision.

#### Objective

Extend an existing factory registry to support a new vehicle type, without modifying the core creation logic inside `create`.

#### Context

The **Factory** pattern is a **creational** pattern. Its role is to centralize object creation so the rest of the code does not need to know which concrete class to instantiate. Instead of scattering `Bus()`, `Train()`, and `Bike()` calls across the codebase, callers ask the factory for a vehicle by name.

A naive factory that grows with every new type looks like this:

```python
def create(self, kind: str):
    if kind == "bus":
        return Bus()
    elif kind == "train":
        return Train()
    elif kind == "scooter":    # must edit here every time
        return Scooter()
```

This violates the **open/closed principle**: the method is never closed for modification. The registry approach solves this — new types are registered from outside, and `create` never changes:

```python
factory.register_kind("scooter", Scooter)
```

In the provided starter file, `VehicleFactory` already manages `Bus`, `Train`, and `Bike` via a `_registry` dictionary. `register_kind(name, cls)` maps a string key to a class; `create(kind)` looks up the key and calls the class with no arguments. The `Scooter` class is defined but not yet registered.

#### Instructions

Copy the starter code from here:

1. Read the existing `VehicleFactory` and `main()`.
2. In `main()`, call `factory.register_kind("scooter", Scooter)` to register the new type.
3. Add `print(factory.create("scooter").mode())` after the existing prints.

Running the code must print exactly:

```text
road
rails
lane
scooter_lane
```

`VehicleFactory.create` must not contain a hardcoded `if kind == "scooter"` branch — the registry does the mapping. Adding a new vehicle type required **zero edits** to existing factory logic.

**Repo:**

* GitHub repository: `holbertonschool-sw_design_architecture`
* Directory: `design_patterns`
* File: `0-factory.py`

---

### 1. Observer - Adding a new subscriber <a name='subparagraph1'></a>

#### Design Problem

Some systems need to react to events without tightly coupling the event source to every possible reaction.

#### Friendly scenario

Consider a news platform that publishes updates. One subscriber may send emails, another may write logs, and another may send SMS alerts only for urgent news. The publisher should not need to know the internal details of each subscriber.

#### Objective

Implement a new observer and subscribe it to a running notification system, filtering it to receive only specific event topics.

#### Context

The **Observer** pattern is a **behavioral** pattern. It defines a one-to-many dependency: when a subject emits an event, all registered observers are notified without the subject knowing their concrete types. This decouples the publisher (who emits) from the listeners (who react), making it easy to add new reactions without touching the publisher.

A tightly coupled alternative hardcodes every listener in the publisher:

```python
def publish(self, headline: str) -> None:
    EmailNotifier().send(headline)
    LogNotifier().write(headline)
```

Adding another reaction in that design would force you to edit the publisher.

With `NewsSubject`, the publisher only calls `self._subject.notify(topic, data)` (it has no knowledge of `LogObserver`, `EmailObserver`, or any future listener). Observers register themselves and declare which topics they care about.

In the provided starter file, `NewsSubject` already implements `subscribe(observer, topics=None)`, `unsubscribe(observer)`, and `notify(topic, data)` with safe snapshot iteration (to handle observers that unsubscribe during a broadcast). `LogObserver` (subscribed to sports and breaking) and `EmailObserver` (subscribed to all topics) are already wired. `SmsObserver` is missing.

#### Instructions

Copy the starter code from here

1. Read the existing `NewsSubject`, `LogObserver`, and `EmailObserver`.
2. Implement `SmsObserver` with an `update(topic, data)` method that prints `sms:<topic>=<data>`.
3. In `main()`, instantiate `SmsObserver` and subscribe it with `topics={"breaking"}` only.

Running the code must print exactly:

```text
email:weather=rain
log:sports=goal
email:sports=goal
log:breaking=alert
email:breaking=alert
sms:breaking=alert
```

`SmsObserver` must react only to `"breaking"` — it must not print for `weather` or `sports` events. Adding it required **zero edits** to `NewsSubject` or any existing observer.

**Repo:**

* GitHub repository: `holbertonschool-sw_design_architecture`
* Directory: `design_patterns`
* File: `1-observer.py`

---

### 2. Decorator - Adding a new wrapper <a name='subparagraph2'></a>

#### Design Problem

When a system has several independent optional features, inheritance can create too many subclasses to manage.

#### Friendly scenario

Imagine a coffee shop system. A customer may want milk, sugar, caramel, or any combination of them. Creating one subclass for every possible combination would quickly become impractical. Wrapping an object lets the system add behavior dynamically.

#### Objective

Add a new decorator that extends a `Beverage` by wrapping it, composing correctly with existing decorators without modifying any existing class.

#### Context

The **Decorator** pattern is a **structural** pattern. It attaches new responsibilities to an object by wrapping it — an alternative to creating a new subclass for each feature combination. With N independent optional features, inheritance would require `2^N` subclasses; decorators require only N wrapper classes that compose freely.

A subclass-based alternative for three toppings would produce:

```text
CoffeeWithMilk
CoffeeWithSugar
CoffeeWithMilkAndSugar
CoffeeWithCaramel
CoffeeWithMilkAndCaramel
...
```

Each decorator instead wraps any `Beverage`, delegates `cost()` and `description()` to `self._inner`, and adds its own contribution. Stacking is done in the constructor call: `MilkDecorator(SugarDecorator(Coffee()))`. The nesting order determines the description order.

In starter code provided, `Coffee` is a concrete `Beverage`. `MilkDecorator` (+10¢, `" + milk"`) and `SugarDecorator` (+5¢, `" + sugar"`) are fully implemented as a model. `CaramelDecorator` is missing.

#### Instructions

Copy the starter code from here

1. Read `MilkDecorator` and `SugarDecorator` as your model.
2. Implement `CaramelDecorator`:

* `cost()` returns `self._inner.cost() + 15`.
* `description()` returns `self._inner.description() + " + caramel"`.

1. In `main()`, add the line that builds `CaramelDecorator(MilkDecorator(SugarDecorator(Coffee())))` and prints its description and cost.

Running the code must print exactly:

```text
Coffee + milk 60
Coffee + sugar + milk 65
Coffee + sugar + milk + caramel 80
```

No existing class is modified, the new behavior lives entirely in `CaramelDecorator`. Adding a new topping required **zero edits** to `Coffee`, `MilkDecorator`, or `SugarDecorator`.

**Repo:**

* GitHub repository: `holbertonschool-sw_design_architecture`
* Directory: `design_patterns`
* File: `2-decorator.py`

---

### 3. Design Patterns Quiz <a name='subparagraph3'></a>

### Objective

Demonstrate understanding of what design patterns are, why the three patterns in this project exist, and how to recognize when to apply each one.

## Quiz Instructions

* This is a **one-shot quiz**
* You will **not be able to retry once submitted**
* Each question has a **time limit**
* Read each question carefully before answering
* Some questions may have **more than one correct answer**

### Instructions

* Questions marked **[single]** have exactly one correct answer.
* Questions marked **[multiple]** have two or more correct answers — you must select all of them.

---


## Authors
Ksyv - [GitHub Profile](https://github.com/ksyv)
