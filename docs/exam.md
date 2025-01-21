# Exam Module

The `exam` module provides tools for generating, managing, and manipulating multiple-choice exams in LaTeX format. It includes classes to represent exams, groups of questions, and individual questions, as well as utility functions to support exam processing.

---

## Classes

### `mc_exam`
#### Overview
Represents an entire multiple-choice exam and provides methods for shuffling questions, generating LaTeX output, and creating answer keys.

#### Attributes
- `filename` (str): Path to the LaTeX file containing the exam.
- `correct_string` (str): The marker used to indicate the correct answer in options. Default is `'CORRECT'`.
- `rng` (numpy.random.Generator): Random number generator for shuffling.
- `elements` (dict): Dictionary of exam elements, either `mc_question` or `mc_group` instances.
- `answer_key` (dict): The generated answer key for the exam.

#### Methods
1. `__init__(exam_file=None, exam_lines=None, correct_string='CORRECT', seed=None)`
   - Initializes an instance of `mc_exam`.

2. `print_exam()`
   - Prints the entire exam, including questions and options.

3. `print_answer_key()`
   - Prints the answer key for the exam.

4. `show_duplicates()`
   - Displays duplicate options in the exam.

5. `exam_to_latex(filename=None)`
   - Exports the exam content to a LaTeX file.

6. `answer_key_to_latex(filename=None)`
   - Exports the answer key to a LaTeX file.

7. `shuffle_questions(filename=None, seed=None, shuffle_within_groups=True)`
   - Shuffles the order of questions and optionally shuffles questions within groups.

8. `shuffle_options(filename=None, seed=None)`
   - Shuffles the options within each question.

9. `shuffle_options_and_questions(filename=None, seed=None, shuffle_within_groups=True)`
   - Shuffles both questions and options.

10. `add_periods(include_equations=True)`
    - Adds periods to the end of options.

11. `capitalize_first()`
    - Capitalizes the first letter of each option.

12. `get_answer_key_letters(option_characters=string.ascii_lowercase, option_character_format='(CHARACTER)')`
    - Retrieves the correct letter for each answer in the answer key.

---

### `mc_group`
#### Overview
Represents a group of multiple-choice questions and provides methods for shuffling questions and options within the group.

#### Attributes
- `group_lines` (list): Lines of LaTeX code for the group.
- `group_string` (str): Full content of the group as a string.
- `group_header` (str): The group header text.
- `group_count` (int): Number of questions in the group.
- `elements` (dict): Dictionary of `mc_question` objects within the group.

#### Methods
1. `__init__(group_lines, correct_string)`
   - Initializes an instance of `mc_group`.

2. `shuffle_questions(rng)`
   - Shuffles the order of questions within the group.

3. `shuffle_options(rng)`
   - Shuffles the options within each question.

4. `add_periods(include_equations=True, correct_string=None)`
   - Adds periods to the end of options.

5. `capitalize_first(correct_string=None)`
   - Capitalizes the first letter of each option.

---

### `mc_question`
#### Overview
Represents a single multiple-choice question with options and associated settings.

#### Attributes
- `question_string` (str): Full LaTeX string for the question.
- `question_header` (str): The header text of the question.
- `options` (list): List of options in the question.
- `all_of_above` (bool): Whether the question includes "All of the above."
- `none_of_above` (bool): Whether the question includes "None of the above."
- `to_shuffle` (bool): Whether the question options should be shuffled.

#### Methods
1. `__init__(question_string=None, correct_string=None)`
   - Initializes an instance of `mc_question`.

2. `shuffle_options(rng)`
   - Shuffles the options of the question if desired.

3. `add_periods(include_equations=True, correct_string=None)`
   - Adds periods to the end of each option.

4. `capitalize_first(correct_string=None)`
   - Capitalizes the first letter of each option.

---

## Functions

### `make_answer_key(exam)`
#### Description
Generates an answer key for a given exam.

#### Args
- `exam` (mc_exam): The exam object containing elements and the correct answer marker.

#### Returns
- `dict`: A dictionary representing the answer key.

## Usage Examples

### Creating an Exam
	
	from exam import mc_exam

	exam = mc_exam(exam_file='sample_exam.tex', correct_string='CORRECT', seed=42)
	exam.print_exam()

### Shuffling Questions

	shuffled_exam = exam.shuffle_questions(seed=123)
	shuffled_exam.exam_to_latex(filename='shuffled_exam.tex')

### Generating an Answer Key

	exam.answer_key_to_latex(filename='answer_key.tex')