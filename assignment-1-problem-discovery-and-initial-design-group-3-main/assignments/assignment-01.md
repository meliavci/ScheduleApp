---
title: "Assignment 1: <Problem Discovery & Initial Design>"
---

# 📑 Cover Page
- **Group Number**: Group 3
- **Student Names**: Melisa Avci, Raphael Tam-Dao, Victor Wilhelmsen, Shehab Wael Abozied Abdelhamed, Aleksandra Wos
- **Course**: DevOps and Low-Code Development
- **Date**: 2025-09-18

---

# Introduction
- **Purpose of the Report**: 
This report provides an introduction to the fundamentals of Business Information Systems (BIS), business process modeling (BPMN), and Lean analysis. Its purpose is to identify real-world problems, analyze them using BIS concepts, and propose an initial system and process design that will be modeled and executed in Camunda.
- **Structure**: 
Section 1. Problem statement & Context 
This section contains a problem statement description, identification of stakeholders and their experience and explanation of our process with the BIS relevance. At the same time we explain what raw data we capture, how the data is useful to the stakeholders, linking it to the DIKW hierarchy and why it’s critical to solving our chosen problem.

Section 2. Theoretical Alignment 
This section classifies the problem into the types of Business Information Systems. We place the system in context and show how data, information, knowledge and wisdom applies by putting it into the DIKW framework. Furthermore we describe the type of change.

Section 3. Business Process Analysis  
This section contains the AS-IS description of the current process. We identified the weaknesses of the process through Lean perspective. We have also created an Ishikawa diagram including four categories: Machine, Data, Human and method. This Ishikawa diagram shows what factors could cause difficulties in the current process. 
Furthermore, we have the TO-BE description, how we would change the current process, where we used Camunda Modeler to make a BPMN model of the new process.     

Section 4. AI Collaboration
This section contains all our logs of the usage of AI as well as a reflection of the usefulness and limitations of AI in our work. 

Section 5. References
This section contains all of our references of the material that we've used for completing this assignment.

---

# Problem Statement & Context
- **Problem Description**: 
Universities and their students face a lot of different challenges in the process of schedule creation. The current system is often managed manually, which makes it both inefficient and time consuming. As a result, timetables are frequently unoptimized and prone to course clashes, especially when students select multiple electives or cross-program courses. This overlap reduces flexibility and limits opportunities for students who want to combine courses from different programs.

Limited room availability and capacity are an additional problem. It is not uncommon for the assigned room to be too small to accommodate the number of students who enrolled in the chosen course. Communication issues further complicate the situation: delays and last-minute changes often prevent updates from reaching students and professors in time, leading to confusion. When a room suddenly becomes unavailable, a professor cancels a class or a new course is added late, making adjustments without creating ripple effects throughout the timetable is particularly difficult.

Another problem lies in the outdated tools many universities still rely on. Despite being slow and error-prone, Excel files and even paper-based scheduling are still in use.

- **Stakeholders**: The stakeholders at the university are students who expect transparency and fairness with as few collisions as possible, professors who expect respect of their availability and management/administration who expect reduced manual work and less time expenditure. They all expect to have a system that is efficient and a system that automatically updates schedules in cases such as cancelled classes, with an automatic real-time notification system.
- **BIS Relevance**: 
The people involved when creating the timetables don’t have any IT expertise. They are schedulers which are only trained to make timetables manually and partly automatically with the given system and by only using data that’s received. The problem now is that the current process is inefficient and they are not capable of improving it because they don’t have all the abilities and tools to do so. The system is working but needs improvement to prevent more clashes. Furthermore, the fact that the university is still partly doing it manually even though they could use algorithms and technologies for it, shows how limited they are in their actions. 

---

# Theoretical Alignment
- **BIS Classification**: 
In our system we use the Transaction Processing System (TPS) to handle routine, day-to-day transactions for example by sending notifications, validating accounts at login or updating the timetables when changes happen. All of these operational tasks are processed automatically. 

The Management Information System (MIS) summarizes and reports data to monitor and control operations. So in our case the system gives us an overview of courses and room usage. Furthermore, users stay up to date by viewing their schedules and changes. It fits into MIS since it provides structured information to help manage teaching activities.

The Decision Support System (DSS) supports decision-making with analysis. Our system uses an algorithm to optimize timetables and minimalizes conflicts. Moreover, it finds suitable rooms with the required equipment. This DSS functionality leads to optimization.

Our system is not primarily ESS, since it doesn’t provide strategic insights and high-level dashboards.
- **DIKW Framework**: 
For the chosen system we need specific data to create a timeschedule with as few clashes as possible. It’s impossible to avoid all clashes and unhappy students but it will be more fair than before because every student will be regarded equally by the system. The data includes attributes for the students, professors and rooms. As well as the general data of the university like opening hours, how long lectures last. 

We want to analyse for example the following: 
- How many students take which course.
- How many lectures are taking place for each student in the semester.
- How many rooms are available when and which type they are.
- Which Professors are available at what time for which course.

After getting an overview over all of the information, it’s easier to understand the system's requirements. We now have to think about how we use this information in our system and manage to accomplish our goal with the data given.

It’s important to think about general knowledge like how to place courses into different time slots considering the break times and opening hours of the university, it’s part of wisdom because we use it to do the action.

Furthermore, we need to figure out how to process the data to achieve as few clashes as possible. For that we have to set up different rules for example to prioritise professors in the system because they are not able to have any clashes in comparison to the students. 

All in all, the decisions we make on what to do are based on the accumulated knowledge and data. It’s important to take all criteria into account and give to the system. The built algorithm needs to get all the data automatically and process it so it’s forming the most optimal timeplan possible for everybody.

Our system transforms raw data, like student’s information, by students logging in with email, to an actionable insights, such as that students can access their schedules. 

- **Organizational Change**: 
Automated notifications about changes and automated creation of scheduling, so it takes less time by not using the human resource. The operation of management becomes automated. Organizations who use paper, whiteboards or manual calendars will transform to our scheduling system, at the same time this changes their current manual operation to everything digital. Introducing the new software is a type of an operational change. In organizations that use excel with bad structure this will be transformed by adopting the new technology. Organizations who use email threads to create the schedule, this new process will be a managerial change. 

At Ostfold University, the departments will no longer be needed as the new solution will be automatic and this is a change to how the management operates currently. The organization of the creation of the timetable for the different student grades happens now in the sorting algorithm instead of a scheduler, this means cutting off the course management completely. Currently students who require adaptation needs are planned for by the management, with the new system it’s accommodated to by retrieving stored information about the adaptation needs and then sorted automatically so no manual work by the management needs to be done. Which room is assigned will be now done automatically, management changes into no management, it’s transformed into automation likewise the operation also becomes automated. 


---

# Business Process Analysis
- **AS-IS Description**: 
The AS-IS process contains inefficiencies, redundancies, and manual work. At our university, the process is as follows: The school (timetable maker) sends information to the professors, informing them that the class information for the next semester must be submitted by a given date. After this, the school collects data from the courses in the “Felles studentsystem” and transfers it to their own timetable system, called “TP”. Next, they group students based on their department and try to minimize scheduling clashes. Once they receive the class information, they begin planning the timetables. Some parts of this process are done manually, while others are handled automatically. Lectures can only be scheduled between 8 a.m. and 4 p.m. Students with special needs are given priority - for example, ensuring that the room is wheelchair accessible. After this, external professors are assigned to their preferred times. The timetables are then created in order: first-year students first, followed by second- and third-year students. The allocation of rooms depends on several factors, such as class size and whether a specialized room is required.

However, at other universities, the system might not be as efficient. There may be even more manual work if the university does not have the resources for a robust system. For example, timetables might be created in Excel, with no systematic comparison across courses, leading to conflicts between courses, rooms, and even professors.

- **TO-BE Description**: 
Our goal is to develop a system that generates the best possible timetables for all students and professors at a university, while minimizing scheduling conflicts. To achieve this, the system evaluates given data about rooms, people, courses, and other relevant resources. Using an algorithm, it then creates the timetable for each course.

We want users to have a clear overview of their courses and always stay up to date. To access the application, they log in with their school account, which the system automatically validates. During this process, the system detects whether the user is a professor, a student, or even a member of the university. If a customer does not have a school account, they cannot use the system to its full extent.

With a valid account, users gain access to features tailored to their role. For students, the system automatically fetches their courses, ensuring they can always view their current timetable. Professors have similar access but with additional options. For example, they can cancel classes on specific dates or change the type of room if certain equipment is needed for a lecture. The system then automatically checks for suitable rooms that meet the requirements and books them.

Whenever changes are made to a timetable, all affected users are notified through the application in time, so they won’t miss any updates.

- **Ishikawa Diagram**:
We identified the weaknesses of the process through the Lean perspective. Based on that, we have created an Ishikawa diagram including the following four categories: Machine, Data, Human and method. This Ishikawa diagram shows what factors could cause difficulties in the current process. 

Humans aren’t perfect by nature, mistakes are hard to avoid, especially when tasks are done manually. Even with the right knowledge and experience, errors are bound to happen. Another issue is resistance to change, which often makes it difficult to introduce and use new systems or processes, even if there are improvements.

The method for creating timetables also matters a lot. It has to follow the university’s policies, regulations and scheduling guidelines. It should also make sure that certain groups like students with special needs are given priority. If the rules are unclear, incomplete, or applied differently by different people, conflicts and inefficiencies can occur.

The timetable software is another important factor. If the system has limitations, errors, or requires too much manual input, the process becomes less efficient and error prone. Problems like downtime, slow performance or poor update notifications can make things worse. If the software is not well designed, a lot of the work will be manual, which increases the chance of mistakes and wastes time.

Finally, the quality of the data used is essential. If the information is incomplete or wrong, it makes the timetable unreliable. For example, student data might have errors like duplicate names or wrong roles, room data might lack details about capacity or accessibility and lecturer data might be missing information about availability or preferences. Without good and reliable data, the timetable will not work properly, no matter how good the people, methods or systems are.
![Ishikawa](../assets/ishikawa.png)

- **BPMN Diagrams**: 
Our BPMN diagram begins with the task “Retrieve data”. Since we do not have an actual database connected, we modeled this as a standard task instead of an SQL task. The next step uses a DMN table filled with dummy data to create the time schedule.

After this, the login process starts. Two exclusive gateways check whether the email exists in the data and whether the password is correct. For our demonstration, we used dummy login data: Email: “a@hiof.de” and password: “12345”. Only with these credentials can the professor log in successfully.

Once logged in, the system generates a personalized timetable from the dummy DMN data. At this point, the professor can choose between different actions. Possible actions include:
- Change room type (restricted to users with the teacher role)
- Cancel class (restricted to users with the teacher role)
- Show timetable in application (available to all users)
- Close the app (available to all users)

The teacher role is verified through an additional gateway to ensure that only professors can modify room types or cancel classes by inputting it in taskforms. These modifications trigger the system to regenerate the timetable and notify users about the changes. Afterwards, the process returns to the “Choose action” task, allowing the professor to continue with further actions.

We decided to model “Show timetable in application” as a user task, even though the system performs the action, because we wanted it to represent the visualization step in the process.

The process ends when the user selects the action “Close the app.”
![BPMN](../assets/bpmn.png)

---

# AI Collaboration
- **Prompt Log**: 
First prompt: Give me business or organizational settings where a workflow or process can be improved by a BIS (Data-oriented app). Examples: construction project document hub, facility maintenance, student event registration, healthcare case management.

Second prompt: You are a scheduler from a university and we were thinking about the problems you're probably facing so we made a list: -Hard for universities to create schedules for students -A lot of times the selected courses clash -There might not be a system that checks if courses clash→ not efficient and time consuming Is there anything you would add to it?

Third prompt: you are the most inefficient time scheduler where students schedules clash for a university, what tools do you use that make it so inefficient.

- **Outputs**: 
First output: Here’s a list of business or organizational settings where a Business Information System (BIS) / data-oriented app could significantly improve workflows or processes:

📂 Document & Information Management
Legal firms → Case file management, legal document versioning, compliance tracking.
Research institutions → Centralized research data hub for collaboration, experiment tracking, and versioned datasets.
Publishing companies → Manuscript submission and review workflows.

🏗️ Operations & Logistics
Construction companies → Construction project document hub (your example), equipment scheduling, and safety inspection reporting.
Logistics & transportation → Fleet tracking, route optimization, cargo documentation.
Warehousing → Inventory tracking, restocking workflows, real-time demand dashboards.

🏥 Healthcare & Social Services
Hospitals/clinics → Patient record case management, staff scheduling, treatment tracking.
Public health departments → Vaccination campaign registration and monitoring.
Non-profits/NGOs → Case tracking for aid distribution, donor data management.

🎓 Education & Campus Life
Universities → Student event registration (your example), course registration optimization, exam room scheduling.
Training organizations → Learning management system for certification and skills tracking.
Research labs → Lab equipment booking, experiment logs, safety protocol tracking.

🏢 Corporate/HR
Human resources → Employee onboarding, leave requests, performance reviews.
Recruitment agencies → Candidate pipeline management, interview scheduling.
Consulting firms → Project resource allocation and deliverable tracking.

🏬 Customer-Facing Services
Hospitality → Hotel facility maintenance (your example), guest request tracking, room service workflows.
Retail → Returns/exchange management, loyalty program data tracking, supply chain analytics.
Event management companies → Ticketing, vendor coordination, volunteer scheduling.

⚙️ Government & Public Sector
Municipal services → Permit applications, building inspections, citizen issue reporting (e.g., potholes, broken streetlights).
Courts → Case assignment, evidence tracking, scheduling of hearings.
Libraries/archives → Digital cataloguing, lending management, research requests.

👉 A useful heuristic: A BIS is especially powerful where there are repetitive, data-heavy processes with multiple stakeholders (documents, approvals, scheduling, compliance, case tracking).

Internal Business Operations
Procurement departments → Supplier database, purchase orders, and contract renewal tracking.
Accounting firms → Client invoice hub, tax document workflow, expense reimbursement tracking.
IT departments → Asset inventory, incident/ticketing system, license renewals.
R&D divisions → Idea submission and evaluation pipeline, patent documentation management.

🏥 Healthcare & Wellness
Mental health clinics → Client intake forms, therapy progress tracking, case notes.
Pharmacies → Prescription management, drug stock tracking, regulatory compliance reporting.
Fitness centers → Member management, trainer schedules, class registration, performance data.

🎓 Education & Training
K-12 schools → Parent-teacher meeting scheduler, student attendance/behavior dashboard.
Universities → Thesis submission and review workflows, lab equipment booking system.
Corporate training → Certification progress tracker, mandatory compliance training hub.

🏗️ Field Services & Maintenance
Utilities companies → Maintenance scheduling (pipes, power lines, meters), outage tracking.
Real estate/property managers → Tenant request system, rent collection dashboards, maintenance logs.
Cleaning/janitorial services → Task assignment, inspection reports, supply inventory.

🚚 Logistics & Supply Chain
Import/export companies → Customs document tracking, shipment compliance.
Food distributors → Expiry date tracking, supplier audits, delivery routing.
E-commerce fulfillment → Order processing workflow, returns/exchange hub.

🎭 Events & Community
Conference organizers → Attendee registration, session scheduling, speaker submissions.
Sports clubs → Player availability, training attendance, match statistics tracking.
Non-profits/volunteer groups → Volunteer shift management, donation/event tracking.

⚖️ Government & Civic Services
Police departments → Case management, evidence chain-of-custody, officer scheduling.
City planning offices → Zoning application workflows, land use data management.
Public libraries → Special event registrations, rare book/archive lending requests.

🌱 Specialized & Niche
Museums → Collection inventory, loan/borrowing agreements, exhibit scheduling.
Farms/agriculture → Crop yield tracking, equipment usage logs, pesticide application records.
Labs/biotech → Sample tracking, experiment workflow automation, compliance logs.
Environmental NGOs → Wildlife sightings data collection, conservation project tracking.

👉 The common thread: anywhere with recurring requests, approvals, scheduling, or regulated documentation → a BIS can replace messy spreadsheets and email threads.
Would you like me to turn this into a master list of 30–40 BIS app scenarios, each with:
Core process (what it improves)
Key entities/data (what’s stored)
Workflow example (how it runs)?
That way, you’d have a catalog of use cases ready for inspiration or project pitching.

Second output: Yes 👌 You’re already hitting the core pain points. If I put myself in the shoes of a university scheduler, I’d add a few more problems that usually come up:

✅ Additional Problems
Room availability & capacity limits → Sometimes two classes are scheduled in the same room, or a room is too small for the enrolled students.
Professor availability → Professors may be double-booked, or schedules ignore their teaching preferences/office hours.
Last-minute changes → When a professor cancels, a room becomes unavailable, or a course is added late, it’s hard to update the schedule without causing ripple effects.
Different student groups → Electives and cross-program courses often overlap, making it hard for students who want to take both.
Manual processes → Many universities still rely on Excel or even paper-based scheduling, which is slow and error-prone.
Exam scheduling conflicts → Students may have two exams at the same time or multiple exams in one day.
Communication delays → Even when the schedule is finalized, updates may not reach students and professors quickly (leading to confusion).
Resource allocation → Some courses need special equipment (labs, projectors), and those rooms may not be managed efficiently.
👉 So, in short: it’s not just about clashes — it’s also about resources, fairness, last-minute changes, and communication.

Third output: If I were the most inefficient university time scheduler, my “tools” and methods would be the exact opposite of what good scheduling software or practices use. Here’s what would make me terrible at it:
Inefficient Tools & Practices
Paper and Sticky Notes

Using scraps of paper and sticky notes instead of a proper system.
Notes fall off, get lost, or overlap, so no one knows when their class really is.
Excel with No Structure
A giant, unformatted spreadsheet with random colors, merged cells, and no filters.
No validation to prevent double-bookings.
Professors and rooms typed inconsistently (“Dr. Smith” in one cell, “Smith, Dr.” in another).
Email Chains & Word Docs
Asking each lecturer to send their availability in long email threads.
Copy-pasting conflicting schedules into Word tables with no automatic conflict detection.
Whiteboard Erased Daily
Writing all classes on a whiteboard with no backup.
Someone erases a section, and suddenly three classes are missing from the schedule.
Random Number Generator
Assigning times and rooms based on dice rolls, coin flips, or a randomizer app.
Leads to classes overlapping, being scheduled at 3 a.m., or crammed into broom closets.
Outdated Software
Using an ancient DOS program from the 1980s that only runs on one old PC.
Requires manual re-entry for every tiny change, with no undo function.
Manual Wall Calendar
Filling in a giant wall calendar by hand, and every time a change is made, crossing things out until the page is unreadable.
Result: impossible to tell which schedule is current.
No Centralized Database
Each department keeps their own schedule in different formats (Word, Excel, Google Docs).
No one compares them, so conflicts between courses, rooms, and professors are guaranteed.

- **Reflection**: 
We've used ChatGPT for brainstorming. Furthermore, we tried to get some help from the AI while working with Camunda Modeler but it wasn't helpful. 
We tried not to use that much AI, so we could decide on our own how the system should work, resulting in a bigger learning process. Though ChatGPT helped us by getting ideas or the perspective of different roles. 
For example, we've used it to tell us what tools could use some improvements or rework out of the scheduler's point of view who is using a less efficient system. The knowledge he gave us was something we didn't have so we either get it from the experience of our scheduler or the AI. 
Because we've already talked to our university about it we only knew about one way to do the creation of the time schedules. ChatGPT on the other hand extended our perspective by adding different scenarios to it. 
In our case we found out that using the AI is usefull for general questions but the AI struggles in more specific scenarios for example in the case of Camunda Modeler it was not able to give us clear structured answers. 

---

# References
- ProcessMaker by Larissa Lewis (2020, November 2). Decision model and notation tutorial | DMN examples. ProcessMaker. https://www.processmaker.com/blog/decision-model-and-notation-dmn-tutorial-examples/
- FSAT. (n.d.). Felles studentsystem (FS) – English pages. Felles studentsystem. https://www.fellesstudentsystem.no/english/index.html
- Wikipedia contributors. (2023, December 30). Student information system. In Wikipedia. https://en.wikipedia.org/wiki/Student_information_system
- Camunda. (2025, January 29). BPMN Gateways and How to Use Them in Camunda [Video]. YouTube. https://youtu.be/yfOXFGlMKjI 
- Camunda. (2021, Juli 01). Camunda Platform 7 Tutorial: Building a Process and Adding Forms in Camunda Run [Video]. YouTube. https://youtu.be/J_ut6-7GUkQ 
- TEKKY TALKS. (2023, January 29). Adding form to user task - Camunda 8 - Camunda BPMN [Video]. YouTube. https://youtu.be/iAbzQSeAgIU
- DecisionSkills . (2014, November 10). How to Solve a Problem in Four Steps: The IDEA Model [Video]. YouTube. https://www.youtube.com/watch?v=QOjTJAFyNrU&t
- i-nexus strategy software. (2018, may 25). The Classic & Reverse Fishbone Diagram | A Whiteboard Training Video  [Video]. YouTube. https://www.youtube.com/watch?v=XinW5dwuKsI 
