# Python Fundamentals — A Tutors Interactive Course

A comprehensive introduction to Python programming built for the [Tutors](https://tutors.dev) open-source learning platform. This course showcases three new Tutors capabilities working together: **interactive Jupyter notebooks** with in-browser Python execution, **Marp slide presentations**, and **Mermaid diagrams**.

## What Makes This Course Different

Traditional online courses present code as static text. This course uses Tutors' new interactive notebook features to let students **write and run Python code directly in the browser** — no local setup required.

### Interactive Exercise Cells

Exercise cells render as fully editable code editors (powered by CodeMirror). Students modify the skeleton code and click **Run** to execute it via [Pyodide](https://pyodide.org/) (Python compiled to WebAssembly). The Python runtime loads once and runs entirely client-side.

### Hidden Solutions with Two-Stage Reveal

Solution cells are hidden by default behind a **Show Solution** button. When clicked, the solution code appears — but the output stays hidden until the student clicks **Run**. This encourages students to read and understand the code before seeing the result.

### Marp Slide Presentations

Each topic opens with a Marp slide deck introducing key concepts. Slides are authored in Markdown and rendered directly in the browser — no PowerPoint or PDF files needed.

### Mermaid Diagrams

Visual notes use Mermaid diagrams (flowcharts, class diagrams, sequence diagrams, mind maps) to illustrate Python concepts like type hierarchies, control flow patterns, and OOP relationships.

## Course Content

| # | Topic | Slides | Notebook | Diagrams | Lab |
|---|-------|:------:|:--------:|:--------:|:---:|
| 1 | Getting Started with Python | yes | 16 cells | yes | — |
| 2 | Variables and Data Types | yes | 20 cells | yes | 4 steps |
| 3 | Operators and Expressions | yes | 19 cells | yes | — |
| 4 | Control Flow | yes | 21 cells | yes | 4 steps |
| 5 | Loops | yes | 23 cells | yes | 4 steps |
| 6 | Functions | yes | 23 cells | yes | 4 steps |
| 7 | Data Structures | yes | 25 cells | yes | 4 steps |
| 8 | File I/O and Error Handling | yes | 23 cells | yes | — |
| 9 | Modules and Packages | yes | 21 cells | yes | — |
| 10 | Object-Oriented Programming | yes | 25 cells | yes | 5 steps |

**Totals**: 10 topics, 10 slide decks, 216 notebook cells (20 exercises + 20 solutions), 18 Mermaid diagrams, 6 labs with 25 steps

## Course Structure

This is a standard Tutors source course using the folder-based authoring format:

```
├── properties.yaml          # Course config
├── course.md                # Course description
├── topic-01-getting-started/
│   ├── topic.md             # Topic title + summary
│   └── unit-1/
│       ├── unit.md          # Unit title
│       ├── talk-1-welcome-to-python/
│       │   ├── talk.md      # Talk title + summary
│       │   └── talk.marp    # Marp slide content
│       ├── notebook-first-program/
│       │   ├── notebook.md  # Notebook title + summary
│       │   └── notebook.ipynb  # Jupyter notebook
│       └── note-1-python-ecosystem/
│           └── note.md      # Markdown with Mermaid diagrams
├── topic-02-variables/
│   └── unit-1/
│       ├── talk-1-variables-types/
│       ├── notebook-variables/
│       ├── note-1-type-system/
│       └── book-variables-practice/   # Lab
│           ├── 00.Variables-Practice.md
│           ├── 01.Setup.md
│           ├── 02.Type-Exploration.md
│           └── ...
└── ... (10 topics total)
```

### Content types

- **Talks** (`talk-N/`): Marp slide decks in `.marp` files with a `talk.md` summary
- **Notebooks** (`notebook-slug/`): Standard `.ipynb` Jupyter notebooks with exercise/solution cell tags
- **Notes** (`note-N/`): Full Markdown documents with embedded Mermaid diagrams
- **Labs** (`book-slug/`): Step-by-step lab guides as numbered Markdown files

### Cell Metadata Convention

Interactive behavior is driven by standard Jupyter cell metadata tags:

```json
{ "metadata": { "tags": ["exercise"] } }
```

- `"exercise"` — renders as an editable CodeMirror editor with Pyodide execution
- `"solution"` — hidden by default with a two-stage reveal (Show Solution → Run)

Any Tutors course can adopt this convention in its notebook cells.

## Building and Running

1. Install the [Tutors CLI](https://github.com/tutors-sdk/tutors-apps-cli):
   ```bash
   npm install -g @tutors/tutors-apps-cli
   ```

2. Generate the course JSON:
   ```bash
   tutors-json
   ```

3. Serve the generated output and open it in the Tutors reader.

Alternatively, to test locally with the Tutors development server:

1. Clone the [Tutors](https://github.com/tutors-sdk/tutors) reader app and run `npm run dev`
2. Serve this course directory:
   ```bash
   npx serve . -p 5501 --cors
   ```
3. Open: `http://localhost:5173/course/localhost:5501`

## Platform Requirements

The interactive notebook features (exercise cells, solution hiding) require the Tutors reader with interactive notebook support merged. Standard Tutors features (Marp slides, Mermaid diagrams, labs) work on the current release.

## License

This course content is provided as a reference implementation for the Tutors platform.
