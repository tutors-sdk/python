---
icon:
  type: mdi:order-numeric-ascending
  color: 00897b
---
# Operator Precedence

When Python encounters an expression with multiple operators, it needs to decide which operations to perform first. This is called **operator precedence** (sometimes called "order of operations").

## The Golden Rule

> When in doubt, use parentheses! They make your code clearer and prevent bugs.

## Precedence Hierarchy

The following diagram shows Python's operator precedence from highest priority (evaluated first) at the top to lowest priority (evaluated last) at the bottom:

```mermaid
flowchart TD
    A["() Parentheses<br/><i>Highest priority - always evaluated first</i>"]
    B["** Exponentiation<br/><i>Right-associative: 2**3**2 = 2**(3**2)</i>"]
    C["+x  -x  ~x Unary<br/><i>Positive, negative, bitwise NOT</i>"]
    D["*  /  //  % Multiplication family<br/><i>Multiply, divide, floor divide, modulo</i>"]
    E["+  - Addition family<br/><i>Add, subtract</i>"]
    F["<<  >> Bitwise shifts<br/><i>Left shift, right shift</i>"]
    G["& Bitwise AND"]
    H["^ Bitwise XOR"]
    I["| Bitwise OR"]
    J["==  !=  <  >  <=  >=  is  in Comparisons<br/><i>All comparisons, identity, membership</i>"]
    K["not Logical NOT<br/><i>Inverts boolean</i>"]
    L["and Logical AND<br/><i>Short-circuits on False</i>"]
    M["or Logical OR<br/><i>Short-circuits on True</i>"]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H
    H --> I
    I --> J
    J --> K
    K --> L
    L --> M

    style A fill:#c8e6c9,stroke:#2e7d32,stroke-width:2px
    style M fill:#ffcdd2,stroke:#c62828,stroke-width:2px
```

## Examples

### Example 1: Arithmetic
```python
result = 2 + 3 * 4 ** 2
# Step 1: 4 ** 2 = 16     (exponentiation first)
# Step 2: 3 * 16 = 48     (multiplication next)
# Step 3: 2 + 48 = 50     (addition last)
```

### Example 2: Mixed operators
```python
result = not 3 > 2 and 5 < 10
# Step 1: 3 > 2 = True        (comparison)
# Step 2: 5 < 10 = True       (comparison)
# Step 3: not True = False     (logical NOT)
# Step 4: False and True = False  (logical AND)
```

### Example 3: With parentheses for clarity
```python
result = (not (3 > 2)) and (5 < 10)   # False
result = not ((3 > 2) and (5 < 10))   # False (different grouping, same result here)
```

## Tips for Beginners

1. **PEMDAS/BODMAS** from math class still applies for arithmetic operators
2. Comparisons have **lower** precedence than arithmetic -- `x + 1 > y` works as expected
3. `not` has **higher** precedence than `and` and `or`
4. `and` has **higher** precedence than `or` -- this matters!
5. When mixing `and` and `or`, **always use parentheses**