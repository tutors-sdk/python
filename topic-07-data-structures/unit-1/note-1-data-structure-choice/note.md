---
icon:
  type: mdi:sitemap-outline
  color: 00897b
---
# Choosing the Right Data Structure

## Decision Flowchart

Use this flowchart when you need to store a collection of data and aren't sure which type to use.

```mermaid
flowchart TD
    A["Need to store\na collection of data?"] --> B{"Need key-value\npairs?"}
    B -->|Yes| C["Use a dict"]
    B -->|No| D{"Need uniqueness?\n(no duplicates)"}
    D -->|Yes| E{"Need it\nimmutable?"}
    D -->|No| F{"Need it\nimmutable?"}
    E -->|Yes| G["Use frozenset"]
    E -->|No| H["Use a set"]
    F -->|Yes| I["Use a tuple"]
    F -->|No| J["Use a list"]

    C --> K["Access: O(1) by key"]
    H --> L["Lookup: O(1)"]
    J --> M["Access: O(1) by index"]
    I --> N["Hashable, can be\na dict key"]
```

## Mutability Map

This diagram groups Python's built-in collections by whether they can be modified after creation.

```mermaid
flowchart LR
    subgraph Mutable["Mutable (can change)"]
        direction TB
        L["list\n[1, 2, 3]"]
        D["dict\n{'a': 1}"]
        S["set\n{1, 2, 3}"]
    end

    subgraph Immutable["Immutable (cannot change)"]
        direction TB
        T["tuple\n(1, 2, 3)"]
        FS["frozenset\nfrozenset({1, 2})"]
        ST["str\n'hello'"]
    end

    Mutable -.->|"Can be converted to"| Immutable
    L -.-> T
    S -.-> FS

    style Mutable fill:#fef3c7,color:#000
    style Immutable fill:#dbeafe,color:#000
```

## When to Use Each

| Use Case | Data Structure | Why |
|----------|---------------|-----|
| Shopping list | **list** | Ordered, items may repeat |
| RGB color | **tuple** | Fixed 3 values, immutable |
| User profile | **dict** | Named fields with values |
| Tags on a post | **set** | No duplicate tags |
| Lookup table | **dict** | Fast key-based access |
| Function returning x, y | **tuple** | Lightweight, immutable |
| Processing queue | **list** | Ordered, append/pop |
| Removing duplicates | **set** | Automatic deduplication |
