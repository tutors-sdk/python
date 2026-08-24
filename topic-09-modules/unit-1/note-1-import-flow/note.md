---
icon:
  type: mdi:import
  color: 00897b
---
# Module Import Flow

Understanding how Python locates and loads modules helps you debug import errors and structure your projects correctly.

## The Import Process

When you write `import mymodule`, Python goes through a specific sequence of steps to find, load, and cache the module:

```mermaid
sequenceDiagram
    participant Script
    participant Cache as sys.modules Cache
    participant Finder as Module Finder
    participant Path as sys.path
    participant Loader as Module Loader

    Script->>Cache: import mymodule
    Cache-->>Script: Already cached?
    alt Module in cache
        Cache-->>Script: Return cached module
    else Module not cached
        Script->>Finder: Find mymodule
        Finder->>Path: Search sys.path entries
        Path-->>Finder: Found at /path/to/mymodule.py
        Finder->>Loader: Load module
        Loader->>Loader: Execute module code
        Loader->>Cache: Store in sys.modules
        Loader-->>Script: Return module object
    end
```

## Package Directory Structure

Packages organize related modules into a directory hierarchy. Here is a typical package layout:

```mermaid
flowchart TD
    A["mypackage/"] --> B["__init__.py"]
    A --> C["module_a.py"]
    A --> D["module_b.py"]
    A --> E["subpackage/"]
    E --> F["__init__.py"]
    E --> G["module_c.py"]

    style A fill:#4a90d9,color:#fff
    style E fill:#4a90d9,color:#fff
    style B fill:#f5a623,color:#fff
    style F fill:#f5a623,color:#fff
    style C fill:#7ed321,color:#fff
    style D fill:#7ed321,color:#fff
    style G fill:#7ed321,color:#fff
```

### Import Examples

| Statement | What It Imports |
|-----------|----------------|
| `import mypackage` | Runs `mypackage/__init__.py` |
| `from mypackage import module_a` | Imports `module_a.py` |
| `from mypackage.subpackage import module_c` | Imports nested module |
| `from mypackage.module_b import func` | Imports a specific name |

### Key Points

- **`__init__.py`** runs when the package is first imported and can define what gets exported
- **`sys.path`** is a list of directories Python searches, in order
- **Caching** in `sys.modules` means each module is executed only once, even if imported many times
- Use **relative imports** (`from . import module_a`) within packages for portability
