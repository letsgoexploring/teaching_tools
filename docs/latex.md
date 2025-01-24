# Lecture Notes, Tables, Figures, and Slides Management Module Documentation

---

## `is_command_available`
Checks if a command is available in the system's PATH.

### Arguments
- `command` (str): The command to check.

### Returns
- `bool`: `True` if the command is available, `False` otherwise.

---

## `make_figure`
Constructs a LaTeX figure environment.

### Arguments
- `image_filename` (str): Path and filename of the image file.
- `position` (str): Position specifier for the figure (`'h'`, `'t'`, `'b'`, `'p'`). Default is `'h'`.
- `caption` (str, optional): Caption for the figure. Default is `None`.
- `label` (str): Label for referencing the figure. Default is an empty string.
- `hspace` (str): Horizontal position offset of the image. Default is `'0cm'`.
- `height` (str): Height of the image. Default is `'6.5cm'`.
- `width` (str, optional): Width of the image. Default is `None`.
- `caption_top` (bool): Whether to place the caption above the figure. Default is `True`.
- `center_image` (bool): Whether to center the image in the figure environment. Default is `True`.
- `filename` (str, optional): Path to save the generated LaTeX figure file. Default is `None`.

### Returns
- `str`: LaTeX string for the figure environment.

---

## `make_tabular`
Constructs a LaTeX tabular environment.

### Arguments
- `data` (`numpy.ndarray`): 2D array with data for the table.
- `table_spec` (str): Column alignment string for the tabular environment. Default is an empty string.
- `row_format` (dict): Row-specific formatting, with keys as row numbers and values as LaTeX formatting commands. Default is `{}`.
- `column_format` (dict): Column-specific formatting, with keys as column numbers and values as LaTeX formatting commands. Default is `{}`.
- `hlines` (list): List of row numbers for horizontal lines. Default is `[]`.
- `clines` (dict): Dictionary for specific clines with row numbers as keys and column range strings as values. Default is `{}`.
- `pos` (str): Vertical positioning specifier (`'b'`, `'c'`, `'t'`). Default is `'c'`.
- `filename` (str, optional): Path to save the LaTeX tabular file. Default is `None`.

### Returns
- `str`: LaTeX string for the tabular environment.

---

## `make_table`
Constructs a LaTeX table environment with a tabular content.

### Arguments
- `data` (`numpy.ndarray`): 2D array with data for the table.
- `table_spec` (str): Column alignment string for the tabular environment. Default is an empty string.
- `row_format` (dict): Row-specific formatting, with keys as row numbers and values as LaTeX formatting commands. Default is `{}`.
- `column_format` (dict): Column-specific formatting, with keys as column numbers and values as LaTeX formatting commands. Default is `{}`.
- `hlines` (list): List of row numbers for horizontal lines. Default is `[]`.
- `clines` (dict): Dictionary for specific clines with row numbers as keys and column range strings as values. Default is `{}`.
- `position` (str): Position specifier for the table (`'h'`, `'t'`, `'b'`, `'p'`). Default is `'h'`.
- `caption` (str, optional): Caption for the table. Default is `None`.
- `label` (str): Label for referencing the table. Default is an empty string.
- `caption_top` (bool): Whether to place the caption above the table. Default is `True`.
- `center_table` (bool): Whether to center the table in the environment. Default is `True`.
- `filename` (str, optional): Path to save the LaTeX table file. Default is `None`.

### Returns
- `str`: LaTeX string for the table environment.

---

## `DataFrame_to_array`
Converts a Pandas DataFrame to a NumPy array, including row and column headers.

### Arguments
- `df` (`pandas.DataFrame`): Input DataFrame.
- `include_index` (bool): Whether to include the index in the output. Default is `True`.
- `include_column_headers` (bool): Whether to include column headers. Default is `True`.
- `keep_index_name` (bool): Whether to keep the index name in the output. Default is `True`.

### Returns
- `numpy.ndarray`: Converted array with headers and index if specified.

---

## `compile`
Compiles LaTeX files in the current directory or specified files.

### Arguments
- `x` (str or list, optional): Filename or list of filenames to compile. If `None`, compiles all `.tex` files in the current directory.

### Deletes
- Auxiliary files generated during compilation.

### Raises
- `RuntimeError`: If `pdflatex` or `bibtex` is not available in the system.

---

## `pdf_latex`
Compiles a LaTeX file using `pdflatex`.

### Arguments
- `file_name` (str): Name of the LaTeX file to compile.

### Raises
- `RuntimeError`: If `pdflatex` or `bibtex` is not available in the system.

---

## `make_handout`
Generates a LaTeX handout file for Beamer slides by modifying the preamble to include the handout option.

### Arguments
- `slides_file_name` (str): Name of the original slides file.
- `handout_file_name` (str): Name of the generated handout file.

---

## `python_script`
Executes a Python script or list of scripts.

### Arguments
- `script` (str or list): Filename or list of filenames for Python scripts.
