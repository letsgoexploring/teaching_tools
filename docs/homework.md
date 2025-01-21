# Homework Class

The `homework` class provides tools to format homework answers in LaTeX or Gradescope-compatible formats.

## Methods

### `__init__(self, filename=None)`
Initializes the `homework` class.

**Args**:
- `filename` (str, optional): Name of the LaTeX file to save answers to. Default is `None`.

### `add_latex_answer(self, name, value, precision=4)`
Adds an answer as a LaTeX command.

**Args**:
- `name` (str): Name of the LaTeX command.
- `value` (str or numeric): Answer to store.
- `precision` (int): Number of decimal places for numeric values. Default is `4`.

### `gs_answer(self, value, tolerance=8, precision=0.005)`
Generates a Gradescope-compatible string.

**Args**:
- `value` (str or numeric): Answer to format.
- `tolerance` (float): Error tolerance. Default is `8`.
- `precision` (float): Rounding precision. Default is `0.005`.

### `write_answer_file(self, filename)`
Exports answers as LaTeX commands in a `.tex` file.

**Args**:
- `filename` (str): Name of the LaTeX file to save answers.