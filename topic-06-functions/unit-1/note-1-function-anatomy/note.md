---
icon:
  type: mdi:puzzle-outline
  color: 00897b
---
# Function Anatomy

## Parts of a Function Definition

This diagram shows the key components that make up a Python function definition.

```mermaid
flowchart TD
    A["def keyword"] --> B["Function Name"]
    B --> C["Parameters\n(name, age=0, *args, **kwargs)"]
    C --> D["Colon :"]
    D --> E["Docstring\n(triple-quoted description)"]
    E --> F["Function Body\n(indented code block)"]
    F --> G{"Has return?"}
    G -->|Yes| H["return value\n(sends result to caller)"]
    G -->|No| I["Returns None\nimplicitly"]

    style A fill:#4a9eff,color:#fff
    style B fill:#34d399,color:#000
    style C fill:#fbbf24,color:#000
    style E fill:#a78bfa,color:#fff
    style F fill:#f97316,color:#fff
    style H fill:#ef4444,color:#fff
    style I fill:#6b7280,color:#fff
```

## LEGB Scope Resolution

Python looks up variable names in four nested scopes. The innermost match wins.

```mermaid
flowchart TD
    subgraph B["Built-in Scope"]
        direction TB
        b1["print, len, range, int, str..."]
        subgraph G["Global Scope (Module)"]
            direction TB
            g1["Module-level variables"]
            subgraph E["Enclosing Scope"]
                direction TB
                e1["Outer function variables"]
                subgraph L["Local Scope"]
                    direction TB
                    l1["Current function variables"]
                end
            end
        end
    end

    style L fill:#ef4444,color:#fff
    style E fill:#f97316,color:#fff
    style G fill:#fbbf24,color:#000
    style B fill:#34d399,color:#000
```

**How it works:**
1. Python first checks the **Local** scope (current function)
2. Then the **Enclosing** scope (any outer functions)
3. Then the **Global** scope (module level)
4. Finally the **Built-in** scope (Python's built-in names)

The first match found is used. Use `global` or `nonlocal` keywords to explicitly write to an outer scope (but prefer passing arguments and returning values instead).
