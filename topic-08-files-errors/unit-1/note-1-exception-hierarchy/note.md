---
icon:
  type: mdi:alert-outline
  color: 00897b
---
# Python Exception Hierarchy

Understanding how Python's exceptions are organized helps you write better error handling code. All exceptions inherit from `BaseException`, but you should almost always catch from `Exception` and its subclasses.

## Exception Class Hierarchy

```mermaid
classDiagram
    BaseException <|-- Exception
    BaseException <|-- KeyboardInterrupt
    BaseException <|-- SystemExit
    Exception <|-- ValueError
    Exception <|-- TypeError
    Exception <|-- KeyError
    Exception <|-- IndexError
    Exception <|-- FileNotFoundError
    Exception <|-- IOError
    Exception <|-- AttributeError
    Exception <|-- RuntimeError
    Exception <|-- StopIteration

    class BaseException {
        +args
        +__str__()
    }
    class Exception {
        Base for all built-in
        non-system-exiting exceptions
    }
    class ValueError {
        Wrong value passed
    }
    class TypeError {
        Wrong type used
    }
    class KeyError {
        Missing dict key
    }
    class IndexError {
        Sequence index out of range
    }
    class FileNotFoundError {
        File or dir not found
    }
    class IOError {
        I/O operation failed
    }
    class AttributeError {
        Missing attribute
    }
    class RuntimeError {
        Generic runtime error
    }
    class StopIteration {
        Iterator exhausted
    }
    class KeyboardInterrupt {
        User pressed Ctrl+C
    }
    class SystemExit {
        sys.exit() called
    }
```

## try / except / else / finally Execution Flow

This diagram shows how Python evaluates each block in the exception handling structure:

```mermaid
flowchart TD
    A[Enter try block] --> B{Exception raised?}
    B -->|Yes| C[Match except clause]
    B -->|No| D[Execute else block]
    C --> E{Handler found?}
    E -->|Yes| F[Execute except block]
    E -->|No| G[Propagate exception up]
    F --> H[Execute finally block]
    D --> H
    G --> H
    H --> I{Was exception handled?}
    I -->|Yes| J[Continue program]
    I -->|No| K[Crash with traceback]
```

### Key Takeaways

- **Never catch `BaseException`** -- this would swallow `KeyboardInterrupt` and `SystemExit`
- **Be specific** with your except clauses -- catch the narrowest exception type possible
- **The `finally` block always runs**, whether or not an exception occurred
- **The `else` block** only runs if no exception was raised in the `try` block
