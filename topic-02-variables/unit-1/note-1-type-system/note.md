---
icon:
  type: mdi:format-list-group
  color: 00897b
---
# Type System Overview

Understanding Python's type system is essential for writing correct programs. This note provides two visual diagrams that illustrate how types are organized and how you can convert between them.

## Python Type Hierarchy

All types in Python inherit from `object`. The diagram below shows the inheritance relationships between Python's built-in types:

```mermaid
classDiagram
    object <|-- int
    object <|-- float
    object <|-- str
    object <|-- NoneType
    object <|-- list
    object <|-- tuple
    object <|-- dict
    object <|-- set
    int <|-- bool

    class object {
        Base class for all Python objects
    }
    class int {
        Whole numbers
        Arbitrary precision
    }
    class float {
        Decimal numbers
        IEEE 754 double
    }
    class str {
        Text sequences
        Immutable
    }
    class bool {
        True or False
        Subclass of int
    }
    class NoneType {
        Singleton None
        Represents absence
    }
    class list {
        Ordered, mutable
        Allows duplicates
    }
    class tuple {
        Ordered, immutable
        Allows duplicates
    }
    class dict {
        Key-value pairs
        Ordered since 3.7
    }
    class set {
        Unordered, unique
        Mutable
    }
```

### Key Insight: bool is a subclass of int

This means `True` is actually `1` and `False` is actually `0`:
```python
>>> True + True
2
>>> False * 10
0
>>> isinstance(True, int)
True
```

## Type Conversion Paths

The following flowchart shows which conversions are possible between Python's core types. Green arrows indicate safe conversions that always succeed. Red arrows indicate conversions that may fail depending on the value.

```mermaid
flowchart TD
    str["str (string)"]
    int_t["int (integer)"]
    float_t["float (decimal)"]
    bool_t["bool (True/False)"]

    str -->|"int('42') - must be valid integer"| int_t
    str -->|"float('3.14') - must be valid number"| float_t
    str -->|"bool('') = False, bool('x') = True"| bool_t

    int_t -->|"str(42) = '42' - always works"| str
    int_t -->|"float(42) = 42.0 - always works"| float_t
    int_t -->|"bool(0) = False, bool(1) = True"| bool_t

    float_t -->|"str(3.14) = '3.14' - always works"| str
    float_t -->|"int(3.9) = 3 - truncates!"| int_t
    float_t -->|"bool(0.0) = False, bool(1.5) = True"| bool_t

    bool_t -->|"str(True) = 'True'"| str
    bool_t -->|"int(True) = 1, int(False) = 0"| int_t
    bool_t -->|"float(True) = 1.0"| float_t

    style str fill:#e1f5fe,stroke:#0288d1
    style int_t fill:#f3e5f5,stroke:#7b1fa2
    style float_t fill:#fff3e0,stroke:#ef6c00
    style bool_t fill:#e8f5e9,stroke:#388e3c
```

### Conversion Tips

1. **str to int/float**: The string must contain a valid number, otherwise you get a `ValueError`
2. **float to int**: Uses truncation (toward zero), not rounding -- use `round()` if you need rounding
3. **Any type to bool**: Empty/zero values are `False`, everything else is `True`
4. **bool to int**: `True` becomes `1`, `False` becomes `0`