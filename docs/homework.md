# Homework Formatting and Export Module Documentation

---

## `homework.__init__(filename=None)`
Initializes an instance of the `homework` class.

### Arguments
- `filename` (str, optional): Name of the LaTeX file to save answers to. Default is `None`.

### Attributes
- `filename` (str): File name for the LaTeX output file.
- `latex_answers` (dict): Dictionary for storing answers as LaTeX commands.

---

## `homework.add_latex_answer(name, value, precision=4)`
Adds an answer as a LaTeX command to the `latex_answers` dictionary.

### Arguments
- `name` (str): Name of the new LaTeX command. Must conform to LaTeX naming conventions.
- `value` (str or numeric): Answer to be stored. Strings are stored as-is, numeric values are formatted.
- `precision` (int): Number of decimal places to round numeric values. Default is `4`.

### Returns
- `None`

---

## `homework.gs_answer(value, tolerance=8, precision=0.005)`
Generates a Gradescope-compatible formatted string for an answer.

### Arguments
- `value` (str or numeric): Answer to format for Gradescope.
- `tolerance` (float): Error tolerance for the answer. Default is `8`.
- `precision` (float): Precision for rounding numeric values. Default is `0.005`.

### Returns
- `str`: A Gradescope-compatible formatted string.

---

## `homework.write_answer_file(filename)`
Exports LaTeX answers as new commands in a `.tex` file.

### Arguments
- `filename` (str): Name of the LaTeX file to save answers to. Appends `.tex` if missing.

### Returns
- `None`
