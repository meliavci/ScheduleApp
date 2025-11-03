[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/AhCPi3Co)
# Course Report Template (Markdown → PDF)

This repository is your report workspace for the course. Write each assignment in Markdown under `assignments/`. At the end of the semester, your final PDF/DOCX is built automatically by GitHub Actions.

## Workflow
- Edit `meta.yaml` with your name, course, semester, etc.
- For each assignment, complete the corresponding file under `assignments/`.
- Add images to `assets/` and reference them in your Markdown.
- Write your end-of-semester synthesis in `final/reflection.md`.
- Push to GitHub. The Action will build `final-report.pdf` and `final-report.docx`.
- Download the artifacts from the run (→ **Actions** tab → latest run → **Artifacts**).

## Local preview (optional)
If you want to preview locally (optional), install Pandoc and a LaTeX engine, then run:

```bash
pandoc \
  assignments/assignment-01.md \
  assignments/assignment-02.md \
  assignments/assignment-03.md \
  assignments/assignment-04.md \
  final/reflection.md \
  --metadata-file=meta.yaml \
  --resource-path=.:assets \
  --pdf-engine=xelatex \
  --toc --toc-depth=2 --number-sections \
  -o final-report.pdf
```


# Timeschedule System Prototype

This project is a Power Apps prototype developed as part of **Assignment 2 – From BPMN to Power Apps Prototype**.
It represents a simplified version of a university **Timeschedule System**, focusing on the student and professor user interfaces rather than the full scheduling backend.

The app demonstrates the transformation of BPMN process steps into a functional Power Apps prototype, emphasizing usability, accessibility, and data integration using Microsoft Dataverse.

## Features

* **Login Screen** – Authenticates the user and identifies their role (student/professor).
* **Timetable Screen** – Displays a mock timetable based on Dataverse data tables (Course, Room, Person, etc.).
* **Profile Screen** – Shows user information and actions depending on their role.
* **Navigation Bar** – Includes a reusable header with a menu, notification bell, and profile icon.
* **Notification Pop-up (Mockup)** – Placeholder for future Power Automate integration.

## Data Integration

* Connected to **Microsoft Dataverse** tables: Person, Course, Enrollment, OpeningHour, Breaktime, Room.
* Uses **dummy data** for testing authentication and screen displays.

## Limitations

* No real authentication or backend logic (mock implementation).
* Notifications and profile actions are not yet functional.
* Future iterations will add timetable optimization and automated notifications.

## Team

* **Melisa** – Timeschedule UI, Dataverse tables, login functionality
* **Raphael** – Login & notification screens, navigation component
* **Victor** – Navbar component design and navigation
* **Aleksandra** – Notification screen design
* **Shehab** – Profile screen design
