# sudoku-sat
# Sudoku SAT Solver with AI Vision Input

An advanced Python application that combines multimodal AI (Gemini Vision API) for automated board OCR extraction with propositional logic (CNF) encoding and Boolean Satisfiability (SAT) solvers to analyze, solve, and visualize Sudoku puzzles.

## Overview
This project bridges artificial intelligence, computer vision, and formal logic. Instead of traditional backtracking algorithms, it translates Sudoku puzzles into Conjunctive Normal Form (CNF) logic formulas and utilizes the **Glucose3 SAT solver** to compute valid solutions, verify puzzle uniqueness, and render results interactively via a Graphical User Interface (GUI) and Matplotlib.

---

## Key Features & Architecture

### 1. AI Vision & OCR Extraction (`image_to_grid`)
- Integrates Google's **Gemini 2.5 Flash API** to process image inputs (PNG, JPG, JPEG) of Sudoku boards.
- Parses unstructured visual data and extracts a clean 9x9 matrix (where `0` denotes empty cells).

### 2. Propositional Logic & CNF Encoding (`encode_sudoku`)
- Encodes Sudoku rules into strict Boolean logic clauses:
  - **Cell Constraints:** Each cell must contain at least one number, and at most one number.
  - **Row & Column Constraints:** Numbers 1-9 must appear uniquely across every row and column.
  - **Subgrid (Box) Constraints:** 3x3 subgrids must satisfy uniqueness rules.
- Translates pre-filled board digits into permanent unit clauses.

### 3. SAT Solving & Uniqueness Checking (`solve_all_solutions`)
- Uses **PySAT (Glucose3)** to solve the CNF formula.
- Employs iterative clause blocking to enumerate *all* valid solutions, enabling puzzle uniqueness verification (applicable to constraint satisfaction problems, scheduling, and formal verification).

### 4. Interactive GUI & Visualization
- Built with **Tkinter** for seamless image selection and error handling.
- Uses **Matplotlib** to plot clean, grid-based graphical representations of solved solutions.

---

## Project Structure
```text
sudoku-sat/
│
├── sudoku_sat_solver.py     # Core script containing OCR, SAT encoding, solver, and GUI
└── README.md                # Project documentation
