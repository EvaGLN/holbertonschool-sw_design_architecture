<div align="center"><img src="https://github.com/ksyv/holbertonschool-web_front_end/blob/main/baniere_holberton.png"></div>

# Introduction to UML Modeling

## Table of Contents :

  - [0. Class Diagram](#subparagraph0)
  - [1. Sequence Diagram](#subparagraph1)
  - [2. Concept Validation Quiz](#subparagraph2)
## Introduction and Context

In this project, you will be introduced to UML (Unified Modeling Language) as a tool to represent software systems.

You will work with a **well-defined problem** and your task will be to:

* analyze the system description
* identify its components
* represent its structure using a **class diagram**
* represent its behavior using a **sequence diagram**

This project is designed to be **automatically validated**, which means:

* all required elements must be correctly identified from the problem
* naming must match exactly
* diagrams must follow the expected structure

This is an **individual project** focused on building your first modeling skills before moving to more open-ended design problems.

---

## Learning Objectives

By the end of this project, you should be able to:

* extract classes, attributes, and methods from a textual description
* model relationships between classes
* determine multiplicity from system rules
* represent a system using UML class diagrams
* model interactions using sequence diagrams
* use Mermaid syntax to express diagrams

---

## Resources

* Introductory UML references (watch/read this first):

    * [UML Class Diagrams](/rltoken/0topIT4Pdz90_jW8n9mcUA)
    * [UML Sequence Diagrams](/rltoken/T94V3pCrRaRJwk6tSE6hvA)

* Mermaid documentation:

    * [Mermaid Class Diagram Documentation](/rltoken/aLTSzUCRwk3GrjqobV-jZA)
    * [Mermaid Sequence Diagram Documentation](/rltoken/qRE2GwYg0oQqGnOcZtr-mw)

### Optional design tools

You may use tools such as **Lucidchart** to sketch your diagrams visually before implementing them in Mermaid.

> ⚠️ Final submission **must be in Mermaid format**

---

## General Requirements

* Environment:

  * Ubuntu 20.04
  * Mermaid-compatible renderer
* Use **Python-style data types** (`str`, `bool`, etc.)
* File names must match exactly
* Do not introduce elements not described in the problem
* Do not rename classes, attributes, or methods
* Diagrams must be **syntactically valid**
* Only include elements that can be justified from the problem statement
* The project will be **automatically corrected**

---

## Problem — Library Loan System

A small library wants to manage its books and users.

The system must allow the library to:

* store information about books
* register users
* create loans when a user borrows a book

### System description

The system revolves around a `Library` that manages books, users, and loans.

Each `Book` has:

* a `title`
* an `author`
* a `state` indicating whether it is available or not (true/false)

Each `User` has:

* a `name`
* an `email`

When a user borrows a book, a `Loan` is created.

Each `Loan` contains:

* a `start_date`
* an `end_date`

### System behavior

The `Library` must be able to:

* `add_book` to its collection
* `register_user`
* `create_loan` when a user borrows a book

When a loan is created:

* the selected book must no longer be available
* the loan must reference the book and the user involved

A `Book` must be able to:

* `mark_as_unavailable`
* `mark_as_available`

A `Loan` must be able to:

* `close_loan`

When a loan is closed:

* the associated book becomes available again

---

## Important note

All the required information to build your diagrams is contained in this description.

You must extract:

* class names
* attributes
* methods
* relationships
* multiplicities

The names used in your diagrams must match exactly the ones provided in the problem.

Do not introduce additional elements.

---

## Hints for modeling

Use the following questions to guide your reasoning:

* Can a `Loan` exist without a `Book`?
* Can a `Loan` exist without a `User`?
* Can a `Book` exist without being loaned?
* Can a `User` exist without having loans?
* If the `Library` is removed, should books and users still exist in the system?
* Which object is responsible for creating a loan?
* Which object is responsible for changing the availability of a book?

---

# Final Notes

This project is intentionally structured to have a **single correct solution**.

You are expected to:

* carefully read the problem
* extract the required elements
* translate them into diagrams

Precision matters.
Small deviations in naming or structure may result in incorrect validation.

This project is your first step into software modeling.
Future projects will be less guided and will allow multiple valid solutions.


## Task
### 0. Class Diagram <a name='subparagraph0'></a>

### Objective

Model the structure of the system using a UML class diagram.

### Instructions

Create a Mermaid class diagram that represents the system described above.

Your diagram must include:

* all relevant classes
* attributes for each class
* methods derived from the described behavior
* relationships between classes
* multiplicities

### Notes

* All names must match exactly those used in the problem statement
* Attribute types must follow Python conventions (`str`, `bool`, etc.)
* Only include elements that are supported by the description

**Repo:**

* GitHub repository: `holbertonschool-sw_design_architecture`
* Directory: `uml_intro`
* File: `0-class_diagram.mmd`

---

### 1. Sequence Diagram <a name='subparagraph1'></a>

### Objective

Model how objects interact when a user borrows a book.

### Use Case

**A user borrows a book from the library**

### Instructions

Create a Mermaid sequence diagram that represents this interaction.

Your diagram must:

* include all relevant participants
* follow the behavior described in the problem
* reflect the correct order of interactions
* use method names exactly as described in the problem statement

### Required interaction flow

Your diagram must represent the following sequence:

1. The `User` requests the `Library` to create a loan
2. The `Library` asks the `Book` to mark itself as unavailable
3. The `Library` creates a `Loan`
4. The `Library` returns confirmation to the `User`

### Sequence diagram conventions (mandatory)

To ensure consistency and allow automatic correction, you must follow these rules exactly:

* Declare at the beginning only the participants that already exist before the interaction starts:
* `User`
* `Library`
* `Book`
* Do **not** declare `Loan` at the beginning of the diagram
* The `Loan` must appear only at the moment it is created using:
`create participant Loan`
* After creation, the `Library` must interact with the `Loan`
* Do not use aliases (`as`) or alternative naming
* Do not add extra participants
* Do not add extra messages beyond those required

### Required final message

The last interaction in the sequence diagram must be exactly:

`Library-->>User: loan created`

Use this message exactly as written:

* sender: `Library`
* arrow: `-->>`
* receiver: `User`
* label: `loan created`

Do not replace it with alternatives such as:

* `Loan created`
* `confirmation`
* `success`
* `return loan`

### Guidance

Consider:

* Which object initiates the process?
* Which object is responsible for creating the loan?
* When is the book marked as unavailable?

### Important notes

* The diagram must be consistent with your class diagram
* All method names must match exactly those defined in the problem
* The diagram must be syntactically valid in Mermaid
* Only one correct solution is expected

**Repo:**

* GitHub repository: `holbertonschool-sw_design_architecture`
* Directory: `uml_intro`
* File: `1-sequence_diagram.mmd`

---

### 2. Concept Validation Quiz <a name='subparagraph2'></a>

### Objective

Validate your understanding of the UML concepts applied in this project.

### Instructions

This quiz evaluates your understanding of:

* class responsibilities
* relationships between objects
* multiplicity
* sequence diagram interpretation
* consistency between structure and behavior

⚠️ Important:

* This is a **one-shot quiz**
* You will have a **time limit for each question**
* Once you answer a question, you cannot change it

Make sure you read each question carefully before answering.

---


## Authors
Ksyv - [GitHub Profile](https://github.com/ksyv)
