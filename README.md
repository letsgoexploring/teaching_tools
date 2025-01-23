# Teaching Tools

`teaching_tools` is a Python module with utilities to assist educators, particularly in higher educatin, with tasks such as managing homework, creating multiple choice exams, sending emails, interacting with Google Calendar, and working with LaTeX files. The utilities for interacting with Gmail and Google Calendar may be useful in contexts outside of education

## Features
- Send and manage Gmail messages.
- Add, find, and delete Google Calendar events.
- Manage and format homework answers for Gradescope.
- Tools for creating multiple choice exams.
- Compile LaTeX files and create handouts for Beamer slides
- Convert Jupyter Notebooks to Python scripts or HTML files.

## Examples
 - [Sending and working with Gmail](docs/gmail.md)


## Documentation
- [Gmail Class](docs/gmail.md)
- [Google Calendar Class](docs/google_calendar.md)
- [Homework Class](docs/homework.md)
- [LaTeX Module](docs/latex.md)
- [Exam Module](docs/exam.md)
- [Standalone Functions](docs/functions.md)

## Installation
	pip install teaching_tools

## Quickstart
	from teaching_tools import homework, gmail, google_calendar

	# Homework
	hw = homework(filename="answers.tex")
	hw.add_latex_answer(name="Q1", value=3.14159)
	hw.write_answer_file("answers.tex")

	# Gmail
	gm = gmail(credentials_path="credentials.json", sender="you@example.com")
	gm.make_message(to="recipient@example.com", subject="Hello", plain_text="Hi there!")

	# Google Calendar
	cal = google_calendar(credentials_path="credentials.json")
	cal.add_event(start="January 1, 2025 9:00 AM", title="New Year Meeting")