---
title: "DevOps and Low-code Development Final Delivery"
---

# Executive Summary
The solution is a Business Information System (BIS) designed to revolutionize university timetable scheduling. It functions as a Decision Support System (DSS) by using an optimization algorithm to generate clash-free timetables .

Assignment 1 (Problem & Context): Focused on analyzing the AS-IS (manual, inefficient) scheduling process through Business Process Modeling (BPMN) and Lean analysis. It established the BIS classification (TPS, MIS, DSS) and applied the DIKW framework to show how raw data is transformed into scheduling wisdom .

Assignment 2 (Prototype): Mapped the BPMN to features, created the data model, and developed a Power Apps prototype to visualize the schedule and enable user actions like class cancellation.

Assignment 3 (DevOps & Automation): Implemented DevOps practices using Azure Boards for planning and management. It established a Power Platform pipeline for Application Lifecycle Management (ALM) and integrated automation with Power Automate flows.

Assignment 4 (Copilot, Monitoring & Deployment): Integrated a Copilot to automate administrative communications (e.g., Student Absence Reporting) and resource management (e.g., Staff Room Change). It included testing and monitoring (using Power Platform Monitor) and the final deployment of the managed solution to a Production environment.

# What problem does your app solve?

The app solves the problem of inefficient, error-prone, and time-consuming manual university timetable scheduling. It eliminates issues like:

- Course Clashes: Timetables that are unoptimized and prone to course overlaps, limiting student flexibility .
- Resource Misallocation: Limited room availability or rooms being too small for enrolled students.
- Communication Delays: Last-minute changes (cancellations, room swaps) often fail to reach students and professors in time, causing confusion.

# Integration Across Assignments
Each assignment was a sequential step that built the theoretical, functional, and operational foundation for the final Business Information System (BIS), moving the project from a conceptual analysis to a deployed, managed solution.

Assignment 1 (Theoretical Foundation): This phase established the project's Problem Statement (manual scheduling and inefficiencies) , defined the AS-IS and TO-BE processes , and used the BIS Classification (DSS, MIS, TPS) and DIKW Framework to solidify the theoretical need for an automated solution.

Assignment 2 (Prototype Development): The BPMN steps from the TO-BE process were translated into app features and a data model (Dataverse tables). This resulted in the creation of the Power Apps prototype for the timetable visualization and core user actions.

Assignment 3 (DevOps and ALM): This phase implemented the DevOps practices necessary to manage the application's lifecycle, using Azure Boards for planning and setting up the Power Platform Pipeline (CI/CD) for Application Lifecycle Management (ALM). It also introduced the first layer of automation via Power Automate flows.

Assignment 4 (Enhancement and Deployment): The final assignment integrated the Copilot for advanced, natural-language automation , performed Testing and Monitoring to validate the solution, and completed the cycle by deploying the final Managed Solution to the Production environment.

# Technical & DevOps Practices
# Version control, branching, CI/CD
The project used a structured Application Lifecycle Management (ALM) system primarily managed through Azure DevOps and Power Platform Pipelines.

- Version Control and Branching: The Power Apps solution, named "TimescheduleApp," was connected directly to the Git repository via Azure DevOps. Changes were manually committed to the Azure Repo after saving in Power Apps Studio. All commits were reviewed before being merged into the main development branch, ensuring a reliable system for tracking every iterative change.

- CI/CD (Continuous Integration/Continuous Deployment): A functional ALM system was established using Power Platform Pipelines. This pipeline was configured to deploy the solution sequentially across environments as a Managed Solution. This practice ensures that the exact, validated version from the Testing environment is moved to Production, which is crucial for stability. The system also enforced a best practice of incrementing the solution version number before deployment, which makes every release traceable.

# Testing/QA
The validation process involved both proactive planning and execution within the Power Platform.

- Testing Execution: Testing was performed using tools like Power Apps Test Studio and the Power Platform Monitor.

- Validation Focus: The testing phase was critical for identifying platform-specific limitations and for verifying functional correctness, such as the successful connection of the Power Automate flows to Dataverse and the correct operation of scheduling logic.
  
# Observability/monitoring (if any)
Monitoring Tool: Power Platform Monitor was used for monitoring.

Outcome: The monitoring did not reveal any decisive bottlenecks but was valuable for understanding platform limitations. The final deployment included a verification step to ensure the core user interfaces (e.g., login screen, timetable) loaded and functioned correctly in the live Production environment.

# Business Impact
# Who are your stakeholders or target users?
The solution delivered a significant shift in how the university operates, moving from reactive maintenance to proactive optimization.

Primary Users: Timetable Schedulers/Staff. Their manual workflow is directly replaced by the automated system.

Other Stakeholders: Professors and Students.

| Stakeholder | Expectations/Outcomes | Impact |
|------------------|----------------------|----------------------------|
|Timetable Schedulers/Staff | Expected significant reduction in manual work and complex task handling.| The role was transformed from a "data entry clerk" to a "decision manager" , shifting focus from maintenance to optimization.| Professors | Expected respect for their availability and automatic, real-time schedule updates/notifications.| The system automated communication (via Copilot and flows) and provided real-time schedule views.| Students | Expected fairness, minimal clashes, and real-time updates for schedule changes.| The system's Decision Support System (DSS) capabilities ensure that optimization logic is used to minimize course conflicts.|

The change implemented was both Operational (shifting from weeks of manual conflict checking to minutes of automated sorting) and Managerial (fundamentally changing how the scheduling department creates value).

# What business outcomes or improvements does your app enable?

Increased Efficiency: Achieves a significant reduction in the manual work and time spent on scheduling.

Shifted Focus: Transforms the Scheduler's role from a "data entry clerk" to a "decision manager," focusing the department's value on optimization rather than maintenance .

Enhanced Student Experience: Provides transparency and fairness with minimal collisions (clashes).

Strategic Agility: Allows the system to automatically reshuffle affected classes with minimal ripple effects when an issue arises (e.g., a room becomes unavailable), improving organizational response time.

# Lessons Learned

- Copilot Integration Limits: A key constraint was the institutional inability to publish the bot, which prevented a seamless, direct integration with the live Power App, forcing the team to use a less efficient workaround.

- Complex Logic Delegation: The team learned that complex relational filtering (e.g., comparing derived fields) is more stable and reliable when the logic is delegated to explicit comparisons (like GUIDs) or normalized values, rather than complex in-app filtering.

- Value of Documentation: The initial structured documentation provided by Azure Boards proved invaluable for tracing back functional requirements to specific tasks, especially when troubleshooting technical conflicts and complex logic.

# Future Work
If you had more time, the following features or improvements would be added, based on the identified limitations and the logical next steps in development:

- Full Copilot Integration and Publishing: Resolve the technical obstacle preventing the bot from being published and directly integrated with the live Power App. This would enable full, live, role-gated natural language transaction handling for all users.

- Automated Notifications: Implement and automate the notification system (currently only a mockup) to provide instant push notifications to all affected students and professors upon any schedule or class change, fully eliminating communication delays.

- Backend Optimization Engine Implementation: Move beyond a draft timetable generation by integrating a robust, dedicated optimization engine that actively calculates the most efficient schedule to minimize student gaps and maximize room usage, as envisioned in the TO-BE process .

- Advanced Data Validation and Standardization: Improve data quality checks, especially addressing incomplete attributes (like specific equipment requirements) and ensuring standardized processes for change requests and conflict prioritization, to reduce reliance on manual workarounds.

## Detailed Teamwork Reflection

Each team member must describe their **own contribution** in detail.

### **Example Guidelines**
When writing your reflection, include:
- What parts of the project you personally developed (e.g., data model, app screens, Power Automate flows, testing, deployment, documentation, etc.)  
- How you contributed to planning, testing, or troubleshooting  
- How you participated in Git commits or DevOps setup  
- Any leadership, coordination, or mentoring roles you took  
---

### **Team Member Contributions**

#### 👤 Member 1 – [Aleksandra Wos]
**Main responsibilities:**  
- Giving inputs to tasks in the assignments where I though needed.
- Doing the taks in the assignment that were given to me.

# Development contributions/What parts of the project you personally developed/What they contributed/Which parts they designed or developed:

In assignment 1: 
- Identify the type of organizational change text

_ Some parts of the stakeholders text

- BPMN modelling together with the rest of the team

In assignment 2: 
- Identifying most of the key requirments from BPMN in our google doc before the text was rewritten in the github template, me and the rest of the team did the mapping.

-Gave imput to Meslia when she was doing the copilot plan designer.

-Power Apps Prototype notifications interface and component low code with help of Raphael  

In assignment 3:

- Defining the tasks in Azure work items and adding them to the github template table.

In assignment 4: 

- For the copilot studio agent I had to do a new power automated flow and I did some parts of the change room topic that used it. The change room agent flow checks room availiabilty after I made it, Raphael made formatting changes to it so that the agent response was readable.

- Gave input on the instructions text in our agent.

For each assignment the whole team gave input to lessons learned part and same with most of the text for the assignments.

The parts I changed after the feeback: for assignment 1 - ishikawa and Melisa helped, helped with BPMN. assignment 2: introductoin to sections 8.3.2 and 8.3.3. and I also did the executive summary.

# Collaboration/How they collaborated with the team:
*(How did you support your teammates?)*  
- Give ideas to the assignments tasks, collaborated where was possible but with the programs used in this course at every stage this was diffuclt because they are not catered to collaboration. 
 
# What did you learn, what challenges did you face, and how did you solve them?  
- For testing in assignment 3 we found out that only one person can do tests at a time because co-authoring gets turned off when one person starts the test, therefore we had to do the tests together even though we originally planned to for each team member to do their own test induvidually. 

# How you contributed to planning, testing, or troubleshooting
As a team we always planned what work we were going to do for our in person meetings

# How you participated in Git commits:
Suggested changes to text in github.

# Any leadership, coordination, or mentoring roles you took:
- I took on the mentoring role when I though my ideas made more sense than what my team members suggested.

---

#### 👤 Member 2 – [Full Name]
**Main responsibilities:**  
*(Describe what you were mainly responsible for)*  

**Development contributions:**  
*(Which features, screens, automations, or AI integrations did you implement?)*  

**Collaboration:**  
*(How did you support your teammates?)*  

**Reflection:**  
*(What did you learn, what challenges did you face, and how did you solve them?)*  

---

#### 👤 Member 3 – [Full Name]
**Main responsibilities:**  
*(Describe what you were mainly responsible for)*  

**Development contributions:**  
*(Which features, screens, automations, or AI integrations did you implement?)*  

**Collaboration:**  
*(How did you support your teammates?)*  

**Reflection:**  
*(What did you learn, what challenges did you face, and how did you solve them?)*  

---

*(Add additional member sections as needed.)*

---

## 7. Sign-off
All team members confirm that:
- The work submitted is original and collaborative.  
- Each member’s described contributions are accurate.

**Signatures / Names:**  
- [Name 1]  
- [Name 2]  
- [Name 3]  
- [Date]

