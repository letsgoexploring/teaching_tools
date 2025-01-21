# LaTeX Tools

This module provides utility functions for managing and compiling LaTeX documents, creating tables and figures, and executing Python scripts.

---

## Functions

### `is_command_available`
**Description:**  
Checks if a given command is available in the system's PATH.

**Args:**
- `command` (str): The command to check.

**Returns:**
- `bool`: `True` if the command is available, `False` otherwise.

---

### `make_figure`
**Description:**  
Constructs a LaTeX figure environment.

**Args:**
- `image_filename` (str): Path and filename of the image file.
- `position` (str): Position specifier for the figure (`'h'`, `'t'`, `'b'`, `'p'`). Default: `'h'`.
- `caption` (str, optional): Caption for the figure. Default: `None`.
- `label` (str): Label for referencing the figure. Default: `''`.
- `hspace` (str): Horizontal offset for the image. Default: `'0cm'`.
- `height` (str): Height of the image. Default: `'6.5cm'`.
- `width` (str, optional): Width of the image. Default: `None`.
- `caption_top` (bool): Place caption above the figure. Default: `True`.
- `center_image` (bool): Center the image in the figure environment. Default: `True`.
- `filename` (str, optional): Save the LaTeX code to a file. Default: `None`.

**Returns:**
- `str`: The LaTeX code for the figure.

---

### `make_tabular`
**Description:**  
Constructs a LaTeX tabular environment.

**Args:**
- `data` (numpy.ndarray): 2D array with data for the table.
- `table_spec` (str): Column alignment for the tabular environment. Default: `''`.
- `row_format` (dict): Row-specific formatting. Keys are row numbers, values are LaTeX commands.
- `column_format` (dict): Column-specific formatting. Keys are column numbers, values are LaTeX commands.
- `hlines` (list): Row numbers to add horizontal lines below. Default: `[]`.
- `clines` (dict): Row numbers as keys, column ranges as values for clines. Default: `{}`.
- `pos` (str): Vertical positioning specifier (`'b'`, `'c'`, `'t'`). Default: `'c'`.
- `filename` (str, optional): Save the LaTeX code to a file. Default: `None`.

**Returns:**
- `str`: The LaTeX code for the tabular environment.

---

### `make_table`
**Description:**  
Creates a LaTeX table environment with tabular content.

**Args:**
- `data` (numpy.ndarray): 2D array with data for the table.
- `table_spec` (str): Column alignment for the tabular environment. Default: `''`.
- `row_format`, `column_format`, `hlines`, `clines` (same as `make_tabular`).
- `position` (str): Position specifier for the table (`'h'`, `'t'`, `'b'`, `'p'`). Default: `'h'`.
- `caption` (str, optional): Caption for the table. Default: `None`.
- `label` (str): Label for referencing the table. Default: `''`.
- `caption_top` (bool): Place caption above the table. Default: `True`.
- `center_table` (bool): Center the table in the environment. Default: `True`.
- `filename` (str, optional): Save the LaTeX code to a file. Default: `None`.

**Returns:**
- `str`: The LaTeX code for the table.

---

### `DataFrame_to_array`
**Description:**  
Converts a Pandas DataFrame to a NumPy array, including row and column headers.

**Args:**
- `df` (pandas.DataFrame): Input DataFrame.
- `include_index` (bool): Include the index in the output. Default: `True`.
- `include_column_headers` (bool): Include column headers. Default: `True`.
- `keep_index_name` (bool): Keep the index name in the output. Default: `True`.

**Returns:**
- `numpy.ndarray`: Converted array.

---

### `compile`
**Description:**  
Compiles LaTeX files in the current directory or specified files.

**Args:**
- `x` (str or list, optional): Filename(s) to compile. If `None`, compiles all `.tex` files in the current directory.

**Raises:**
- `RuntimeError`: If `pdflatex` or `bibtex` is unavailable.

**Deletes:**  
Removes auxiliary files generated during compilation.

---

### `pdf_latex`
**Description:**  
Compiles a LaTeX file using `pdflatex`.

**Args:**
- `file_name` (str): LaTeX file to compile.

**Raises:**
- `RuntimeError`: If `pdflatex` or `bibtex` is unavailable.

---

### `make_handout`
**Description:**  
Creates a handout version of Beamer slides by modifying the preamble.

**Args:**
- `slides_file_name` (str): Original slides filename.
- `handout_file_name` (str): Name of the generated handout file.

---

### `python_script`
**Description:**  
Executes a Python script or a list of scripts.

**Args:**
- `script` (str or list): Filename(s) of the script(s) to execute.

---

### Usage Examples

#### Create a Figure

   ```figure_code = make_figure(image_filename='example.png',caption='This is an example figure.',label='fig:example',height='5cm',width='10cm')```
   ```print(figure_code)```