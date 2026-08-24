---
icon:
  type: mdi:relation-many-to-many
  color: 00897b
---
# OOP Relationships

Object-oriented design involves choosing the right relationships between classes. The two most important are **inheritance** (is-a) and **composition** (has-a).

## Class Diagram: Inheritance and Composition

This diagram shows how `Dog` and `Cat` inherit from `Animal` (is-a), while `Owner` has a composition relationship with `Animal` (has-a):

```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +speak() String
        +__str__() String
    }

    class Dog {
        +String breed
        +speak() String
        +fetch(item) String
    }

    class Cat {
        +bool indoor
        +speak() String
        +purr() String
    }

    class Owner {
        +String name
        +List~Animal~ pets
        +add_pet(animal)
        +list_pets() String
    }

    Animal <|-- Dog : inherits
    Animal <|-- Cat : inherits
    Owner o-- Animal : has many
```

## The Four Pillars of OOP

```mermaid
flowchart LR
    OOP["Object-Oriented
Programming"]

    E["Encapsulation

Bundle data and methods
together. Hide internal
state behind an interface."]
    A["Abstraction

Expose only essential
features. Hide complex
implementation details."]
    I["Inheritance

Create new classes from
existing ones. Share and
extend behavior."]
    P["Polymorphism

Same interface, different
behavior. One method
name, many forms."]

    OOP --> E
    OOP --> A
    OOP --> I
    OOP --> P

    style OOP fill:#4a90d9,color:#fff
    style E fill:#7ed321,color:#fff
    style A fill:#f5a623,color:#fff
    style I fill:#d0021b,color:#fff
    style P fill:#9013fe,color:#fff
```

### Quick Reference

| Principle | Key Idea | Python Example |
|-----------|----------|----------------|
| **Encapsulation** | Hide internals | `_private` attributes, `@property` |
| **Abstraction** | Simplify interface | Abstract base classes (`ABC`) |
| **Inheritance** | Reuse behavior | `class Dog(Animal)` |
| **Polymorphism** | Flexible behavior | Override `speak()` per subclass |
