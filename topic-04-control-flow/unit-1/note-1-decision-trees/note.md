---
icon:
  type: mdi:file-tree-outline
  color: 00897b
---
# Decision Trees

## How `if/elif/else` Executes

The following flowchart shows how Python evaluates an `if/elif/else` chain from top to bottom, executing only the first matching branch.

```mermaid
flowchart TD
    A["Evaluate Condition"] --> B{"if condition_1?"}
    B -->|True| C["Execute if block"]
    B -->|False| D{"elif condition_2?"}
    D -->|True| E["Execute elif block"]
    D -->|False| F{"elif condition_3?"}
    F -->|True| G["Execute elif block 2"]
    F -->|False| H["Execute else block"]
    C --> I["Continue program"]
    E --> I
    G --> I
    H --> I
```

**Key insight:** Only **one** branch ever executes. Once a condition matches, all remaining conditions are skipped entirely.

---

## `if/elif/else` vs `match/case`

This diagram compares when to use each pattern for decision-making.

```mermaid
flowchart TD
    A["Need to make a decision?"] --> B{"What kind of check?"}
    B -->|"Range/comparison\n(>, <, >=, etc.)"| C["Use if/elif/else"]
    B -->|"Exact value matching"| D{"How many values?"}
    B -->|"Structure/pattern\nmatching"| E["Use match/case"]
    D -->|"2-3 values"| C
    D -->|"Many values"| F["Use match/case"]
    C --> G["Example:\nif score >= 90:\n    grade = A"]
    E --> H["Example:\nmatch point:\n    case 0, y: ..."]
    F --> I["Example:\nmatch command:\n    case quit: ..."]
```

**Rules of thumb:**
- Use `if/elif/else` for **comparisons** and **ranges**
- Use `match/case` for matching **specific values** or **destructuring data**
- For just 2-3 exact values, `if/elif` is perfectly fine
