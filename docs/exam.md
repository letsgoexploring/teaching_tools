# Multiple Choice Exam Management Module Documentation

---

## `make_answer_key(exam)`
Creates an answer key for the given multiple-choice exam.

### Arguments
- `exam` (`mc_exam`): An exam object containing elements, options, and a `correct_string` to identify correct answers.

### Returns
- `dict`: A dictionary representing the answer key.

---

## `mc_question` Class
Defines a class for storing and managing the content of a multiple-choice question.

### `__init__(question_string=None, correct_string=None)`
Initializes an `mc_question` instance.

#### Arguments
- `question_string` (str, optional): The full content of the multiple-choice question, including options. Defaults to `None`.
- `correct_string` (str, optional): The marker indicating the correct answer. Defaults to `None`.

---

### `shuffle_options(rng)`
Shuffles the options of the question if shuffling is enabled.

#### Arguments
- `rng` (`numpy.random.Generator`): A random number generator for shuffling.

#### Returns
- `mc_question`: A new instance with shuffled options.

---

### `add_periods(include_equations=True, correct_string=None)`
Adds periods to the end of each option if not already present.

#### Arguments
- `include_equations` (bool, optional): Whether to add periods for options ending with equations. Defaults to `True`.
- `correct_string` (str, optional): The marker for the correct answer. Defaults to `None`.

---

### `capitalize_first(correct_string=None)`
Capitalizes the first letter of each option.

#### Arguments
- `correct_string` (str, optional): The marker for the correct answer. Defaults to `None`.

---

## `mc_group` Class
Defines a class for storing and managing a group of multiple-choice questions.

### `__init__(group_lines, correct_string)`
Initializes an `mc_group` instance.

#### Arguments
- `group_lines` (list): Lines from a LaTeX file between `\begin{mcquestions}` and `\end{mcquestions}`.
- `correct_string` (str): The marker indicating the correct answer for the group.

---

### `shuffle_questions(rng)`
Shuffles the order of questions within the group.

#### Arguments
- `rng` (`numpy.random.Generator`): A random number generator for shuffling.

#### Returns
- `mc_group`: A new instance with shuffled questions.

---

### `shuffle_options(rng)`
Shuffles the options for each question in the group.

#### Arguments
- `rng` (`numpy.random.Generator`): A random number generator for shuffling.

#### Returns
- `mc_group`: A new instance with shuffled options.

---

### `add_periods(include_equations=True, correct_string=None)`
Adds periods to the end of options in all questions.

#### Arguments
- `include_equations` (bool, optional): Whether to include periods for options ending with equations. Defaults to `True`.
- `correct_string` (str, optional): The marker for the correct answer. Defaults to `None`.

---

### `capitalize_first(correct_string=None)`
Capitalizes the first letter of each option in all questions.

#### Arguments
- `correct_string` (str, optional): The marker for the correct answer. Defaults to `None`.

---

## `mc_exam` Class
Defines a class for storing the content of a multiple-choice exam.

### `__init__(exam_file=None, exam_lines=None, correct_string='CORRECT', seed=None)`
Initializes an `mc_exam` instance.

#### Arguments
- `exam_file` (str, optional): Path to the exam LaTeX file.
- `exam_lines` (list, optional): List of lines from the exam LaTeX file.
- `correct_string` (str): Marker string indicating the correct answer.
- `seed` (int, optional): Random seed for reproducibility.

---

### `print_exam()`
Prints the content of the exam to the console.

---

### `print_answer_key()`
Prints the answer key for the exam to the console.

---

### `show_duplicates()`
Displays any duplicate options in the exam questions.

---

### `exam_to_latex(filename=None)`
Exports the exam content to a LaTeX file.

#### Arguments
- `filename` (str, optional): Path to save the LaTeX file. Defaults to the original filename with an appended suffix.

---

### `answer_key_to_latex(filename=None)`
Exports the answer key to a LaTeX file.

#### Arguments
- `filename` (str, optional): Path to save the LaTeX file. Defaults to the original filename with an appended suffix.

---

### `shuffle_questions(filename=None, seed=None, shuffle_within_groups=True)`
Shuffles the questions in the exam.

#### Arguments
- `filename` (str, optional): Path to save the shuffled exam.
- `seed` (int, optional): Random seed for reproducibility.
- `shuffle_within_groups` (bool): Whether to shuffle questions within groups.

#### Returns
- `mc_exam`: A new instance with shuffled questions.

---

### `set_seed(seed=None)`
Sets the random seed for reproducibility.

#### Arguments
- `seed` (int, optional): Random seed value.

---

### `shuffle_options(filename=None, seed=None)`
Shuffles the options within each question.

#### Arguments
- `filename` (str, optional): Path to save the shuffled exam.
- `seed` (int, optional): Random seed for reproducibility.

#### Returns
- `mc_exam`: A new instance with shuffled options.

---

### `shuffle_options_and_questions(filename=None, seed=None, shuffle_within_groups=True)`
Shuffles both questions and options in the exam.

#### Arguments
- `filename` (str, optional): Path to save the shuffled exam.
- `seed` (int, optional): Random seed for reproducibility.
- `shuffle_within_groups` (bool): Whether to shuffle questions within groups.

#### Returns
- `mc_exam`: A new instance with shuffled options and questions.

---

### `add_periods(include_equations=True)`
Adds periods to the end of sentences in the exam answer choices.

#### Arguments
- `include_equations` (bool): Whether to include equations in the operation.

---

### `capitalize_first()`
Capitalizes the first letter of each sentence in the exam answer choices.

---

### `get_answer_key_letters(option_characters=string.ascii_lowercase, option_character_format='(CHARACTER)')`
Retrieves the correct letter for each answer in the key.

#### Arguments
- `option_characters` (str): Characters used to represent options.
- `option_character_format` (str): Format string for option characters.

#### Returns
- `list`: Answer key in letter format.
