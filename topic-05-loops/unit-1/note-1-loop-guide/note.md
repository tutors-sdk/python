---
icon:
  type: mdi:compass-outline
  color: 00897b
---
# Loop Decision Guide

Use this flowchart to decide which loop construct to use in Python.

```mermaid
flowchart TD
    A["Need to repeat something?"] --> B{"Know how many\ntimes?"}
    B -->|Yes| C{"Iterating over\na collection?"}
    B -->|No| D["Use while loop"]
    C -->|Yes| E{"Need the index?"}
    C -->|No| F["Use for i in range(n)"]
    E -->|Yes| G["Use enumerate()"]
    E -->|No| H["Use for item in collection"]
    D --> I{"Need user input\nor event?"}
    I -->|Yes| J["while True: + break"]
    I -->|No| K["while condition:"]
    H --> L{"Building a new\nlist/dict/set?"}
    G --> L
    F --> L
    L -->|Yes| M["Consider a\ncomprehension"]
    L -->|No| N["Regular loop\nis fine"]
    M --> O{"Simple transform\nor filter?"}
    O -->|Yes| P["Use comprehension"]
    O -->|No, complex logic| N
```

## Quick Reference

| I want to... | Use this |
|---|---|
| Loop over a list | `for item in my_list` |
| Loop with index | `for i, item in enumerate(my_list)` |
| Loop N times | `for i in range(n)` |
| Loop until condition | `while condition` |
| Loop over two lists | `for a, b in zip(list1, list2)` |
| Build a new list | `[expr for item in iterable]` |
| Build a new dict | `{k: v for item in iterable}` |
| Find first match | `for + break` or `next()` |
