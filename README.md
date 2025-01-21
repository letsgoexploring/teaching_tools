# Teaching Tools

`teaching_tools` is a Python module designed to assist educators with tasks such as managing homework, sending emails, interacting with Google Calendar, and working with LaTeX files. 

## Features
- Manage and format homework answers in LaTeX or Gradescope.
- Send and manage Gmail messages.
- Add, find, and delete Google Calendar events.
- Convert Jupyter Notebooks to Python scripts or HTML files.
- Tools for working with LaTeX and exams.

## Documentation
- [Homework Class](docs/homework.md)
- [Gmail Class](docs/gmail.md)
- [Google Calendar Class](docs/google_calendar.md)
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