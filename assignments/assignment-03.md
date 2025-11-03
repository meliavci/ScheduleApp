# Assignment 3 – DevOps Planning, Pipeline, and Automation

## DevOps Planning (Azure Boards)

### Project Setup
Describe how you created your Azure DevOps (ADO) project and connected it to your GitHub repository.
Include the name of your Power Apps solution and explain how the integration supports version control.

**Screenshot:** Azure DevOps project overview with project stats from the right side of the screen.
The Git repository address that you used for your apps. I have created a new folder named "powerapps-solution" in your current repository, where you can use to connect to Power Apps.

### Work Items Definition
List your **Epics**, **Issues/User Stories**, and **Tasks**.

| Epic | Description | Related Issues |
|------|--------------|----------------|
| Schedule optimization App | To develop an efficient and automated scheduling system that minimizes course clashes, optimizes room usage, and improves communication between students and staff. The system should replace outdated manual methods, reduce errors, and ensure timely updates for all timetable changes. | The user wants to view their timetable within the application interface, The user wants to choose an action from the available options in the application,  The scheduler wants to retrieve the user data, The scheduler wants to generate a personalized timetable for the user, The user wants to log in to the application to access their personal timetable, The professor wants to change the room type for a scheduled class so that the room gets updated, The professor wants to cancel a class from the timetable, The user wants to get notified by the system about any timetable or class changes, The user wants to log out of the application, The user wants to navigate through screens |

| Issue | Description | Related Task(s) |
|-------|--------------|-----------------|
| The user wants to view their timetable within the application interface. | Implement a visible, dynamic schedule interface for the user's current timetable. | Create frontend component to display timetables, Update timetable dynamically after room change, Test timetable generation for conflicts, Display the generated personalized timetables, Integrate timetable generation with user data, Design database structure and create tables in Dataverse, Create scheduled update of the course status everyday |
| The user wants to choose an action from the available options in the application. | Create buttons from which users can select role-specific functions. | Create the profile page UI, Implement backend logic for class cancellation, Implement backend endpoint to update room details, Test all user actions for proper handling, Add UI option for changing room type |
| The scheduler wants to retrieve the user data. | Ensure the system can connect to and retrieve all necessary course, person, and room information. | Design database structure and create tables in Dataverse |
| The scheduler wants to generate a personalized timetable for the user. | Find a way to build an optimized schedule with minimal conflicts. | Test timetable generation for conflicts, Integrate timetable generation with user data, Design database structure and create tables in Dataverse |
| The user wants to log in to the application to access their personal timetable. | Build the login interface and authentication logic. | Implement routing after successful login, Test login flow, Implement login logic, Design login page UI |
| The professor wants to change the room type for a scheduled class so that the room gets updated. | Implement a feature allowing professors to modify room requirements for their class sessions. | Implement backend endpoint to update room details |
| The professor wants to cancel a class from the timetable. | Implement the necessary action and subsequent flow to allow a professor to cancel a scheduled class. | Implement backend logic for class cancellation |
| The user wants to get notified by the system about any timetable or class changes. | Establish a real-time notification mechanism to inform users of schedule or class alterations | Create the notification UI, Test notification functionality, Create backend logic when changes happen |
| The user wants to log out of the application. | Implement the functionality for the user to securely end their session. | Test logout process, Implement the logout backend, Implement log out logic |
| The user wants to navigate through screens. | Implement clear and functional navigation elements to allow the user to move between different views and sections of the app. | Implement the routing of the navigation bar, Create the frontend of the navigation bar |


| Task | Assignee | Status | Notes |
|------|-----------|--------|-------|
| Create the profile page UI | Melisa, Shehab | Done | Create a profile interface with buttons to choose actions as "Change room type", "Log out" and "Cancel class". Also display the user's name, courses, email and role. |
| Test login flow | Melisa | Doing | Validate successful and failed login attempts. |
| Implement login logic | Melisa | Done | Build backend endpoints for secure login (email/password) with proper user feedback for invalid credentials or missing fields and connect it to the frontend. |
| Test logout process | / | To Do | Ensure logout works properly. |
| Implement the logout backend | / | To Do | When a user clicks on the logout button their status should change in the database and they should be directed to the log in page. |
| Create the notification UI | Aleksandra, Melisa | Done | Create a notification component which tells the updated changes in the user's timetable. |
| Implement routing after successful login | Melisa | Done | When logging in and the user's credential match then they should be navigated to the timetable page. |
| Create scheduled update of the course status everyday | Melisa | Done | Check if the past day has cancelled classes and setting the "Taking place?" column of the courses back to "yes" with a Power Automate flow. |
| Design database structure and create tables in Dataverse | Melisa | Done | Define how courses, break times, rooms, enrollments, opening hours and persons are stored to support personalized timetable generation in a table in Dataverse and filling out the tables with data. |
| Test timetable generation for conflicts | Melisa | Done | Verify that the generated schedules are accurate, clash-free, and efficient by using some test data. |
| Implement the routing of the navigation bar | Raphael, Melisa, Victor, Aleksandra | Done | Add routing logic to the buttons of the navigation bar component (Timetable page, Profile page, Notifications). |
| Create the frontend of the navigation bar | Victor, Melisa | Done | Create the navigation bar with three buttons (Timetable, Profile and Navigation). |
| Design login page UI | Melisa, Raphael | Done | Create a clean and intuitive interface for user authentication as a new login form component with the fields "email" and "password". |
| Create frontend component to display timetables | Melisa | Done | Build the visual interface showing a timetable as a new component. |
| Integrate timetable generation with user data | Melisa | Done | Connect the algorithm to user course selections and preferences from the Dataverse database with a Power Automate flow. |
| Implement log out logic | / | To do | Navigate the user to the log in page when clicking on the "Log out" button. |
| Display the generated personalized timetables. | Melisa | Done | Connect the data of each user's generated timetable to their timetable frontend component. |
| Implement backend logic for class cancellation | Melisa | Done | Create database handling for canceled classes. |
| Test notification functionality | Melisa | Doing | Confirm the affected users get notified directly when a change in their timetable happens. |
| Create backend logic when changes happen. | Melisa | Done | Notify affected users about changes in their timetable. |
| Update timetable dynamically after room change | / | To Do | Ensure affected timetable frontend update in real time after editing. |
| Implement backend endpoint to update room details | / | To Do | Check for available rooms for the specific time and type and update the data to the timetable. |
| Add UI option for changing room type | / | To Do | Create a scheduler-only interface to modify the room for a class. |
| Test all user actions for proper handling | Melisa | Doing | Check that every option triggers the correct function. |


**Screenshot:** Azure Boards (To-do, Doing, Done), feel free to add your sprints too.

### Planning and Collaboration
Explain how you used Azure Boards to plan, manage and visualize team work.  
Reflect on how this improved collaboration compared to previous assignments (where tasks may have been less structured).

#### Planning, Management, and Visualization with Azure Boards
We used Azure Boards as our central repository for all work items, ensuring we had a hierarchical structure that linked business requirements to code implementation.
##### 1. Work Item Hierarchy and Scope
We mapped our project requirements using the standard Azure DevOps hierarchy:
Epics: These represented the major, overarching goal of the project 
Issues/User Stories: These defined the core functional requirements from the perspective of the users (scheduler, professor, student, etc.), such as "The user wants to view their timetable."
Tasks: These were the concrete, technical steps required to complete an Issue (e.g., Create Dataverse table: Person, Implement X/Y Positioning Formula).
By defining these items, we visualized the full scope of the assignment, from the highest requirement down to the smallest coding change.
##### 2. Management and Workflow Visualization
We primarily used the Boards view to manage our workflow, although our process was fluid:
Boards View: The main board provided a visual overview of what was in progress, finished, or upcoming. This immediately showed us which functional areas (Issues) were lagging.
Task Definition: We followed the standard practice of adding tasks for work we had already completed (to ensure the documentation was accurate) and adding tasks for future work without rigid assignment.
Flexible Assignment: We did not assign tasks to specific individuals prematurely. Instead, an individual would spontaneously decide to pick up a task during or after a meeting, ensuring that ownership was based on immediate capacity and relevant skill, not a rigid schedule.
This structure allowed us to maintain traceability if a block was incorrectly positioned on the timetable, we could trace it back to the Issue and the corresponding Task.
#### Reflection on Collaboration Improvement
In previous assignments, because we primarily worked together in meetings, we generally all knew the status of tasks, making the formal tracking less critical. For this assignment, however, we had a few more divided tasks.
Despite this, using the status columns and assignment features of Azure Boards did not drastically improve our collaboration day-to-day, especially since most of us generally knew which tasks were done or in progress.
The main benefit of Azure Boards for this assignment was providing a structured system for documenting our logic and confirming the final scope. Having the full list of Issues and Epics documented in one place, instead of just relying on spontaneous ideas or memory, ensured we didn't forget critical requirements before the final submission.
This approach using the board as a comprehensive documentation and scoping tool was ultimately the most valuable aspect for completing the assignment successfully.


---

## Power Apps Pipeline Setup

### Environment Structure
Describe the environments you used in your pipeline:


### Pipeline Configuration
Explain the Power Apps pipeline stages, triggers, and approvals (if any).

**Screenshot(s):** Power Apps pipeline setup (each stage visible).

**Short Explanation:**
- What does each stage do?
- How is deployment triggered?
- How does this pipeline ensure version control?

### Lessons Learned
Briefly describe what worked well and any limitations or errors faced during pipeline creation.

---

## Automation with Power Automate

### Flow Description
Explain the purpose of your Power Automate flow.

#### Flow Analysis: Cancel_Course_Notification
##### Flow Description
This instant cloud flow is triggered manually from the Power App (by the professor) to instantly cancel a selected class session in the backend and notify all affected students.
This flow is triggered instantly from the Power App and updates the course status to 'Cancelled' while sending a push notification to every enrolled student about the schedule change.
##### Short Explanation
- What does the flow automate? The flow automates three critical steps: 1) Updating the course status (Column: “Taking place?”) in the Dataverse Courses table to "No" (Cancelled). 2) Identifying all affected students by querying the Enrollments table. 3) Sending a personalized push notification to the mobile device of every enrolled student.
- Why is it useful for your solution? This flow directly solves the problem of communication delays and ripple effects caused by manual scheduling changes. It ensures that the database reflects the cancellation immediately, and all stakeholders (students) are notified in real-time, fulfilling the expectation for an automatic, real-time notification system.
- How did you test it? The flow was tested by executing the final OnSelect logic of the "Select" button in the Power App. We verified that: 1) The flow ran without error. 2) The target course in the Courses table successfully changed its status (e.g., from 'Yes' to 'No'). 3) The test user (student) received the push notification on their mobile device. 4) The timetable block in the Power App immediately displayed the "Cancelled" icon (due to the Visible property logic) after the screen refresh.

#### Flow Analysis: Reset_Cancelled_Courses_Daily
##### Flow Description
This scheduled cloud flow runs once daily to clean up the schedule by resetting the status of courses whose cancellation day has passed, ensuring they are automatically available for the next scheduled week.
This flow is triggered on a daily recurrence to check for courses marked as 'No' (Cancelled) whose class day is over, automatically resetting their status to 'Yes' (Scheduled).
##### Short Explanation
- What does the flow automate? The flow automates the status reset of courses. It runs every night (e.g., at 23:45), lists all courses currently marked as "No" (Cancelled), and then checks the course's Weekday against the current day. If the class day has just ended, the flow updates the course's "Taking place?" status back to 'Yes' (Scheduled).
- Why is it useful for your solution? This flow solves the issue of manual schedule adjustments and data hygiene. Without it, a course cancelled one Monday would remain marked as 'No' indefinitely, requiring manual intervention to make it appear on the schedule the following week. The flow ensures the timetable remains accurate and future scheduling is unhindered.
- How did you test it? The flow was tested manually by: 1) Setting a test course's status in Dataverse to 'No'. 2) Manually triggering the scheduled flow. 3) Temporarily adjusting the date and time inside the flow's condition logic to force a comparison with the course's specific Weekday. 4) Verifying that the course's status was successfully updated back to 'Yes' (1).


**Flow Diagram or Screenshot:** Flow steps and trigger.

---

## Reflection

Reflect on your overall DevOps experience.

- How did **Azure Boards** help organize work and improve efficiency?
- What went well with **pipeline deployment and automation**?
- What were the main challenges and lessons learned?
- How does this DevOps approach differ from your earlier development process?

#### Azure Boards: Organization and Efficiency
Azure Boards served as our central documentation and visualization tool. While our team often worked collaboratively in meetings and had a flexible assignment style, the platform provided necessary structure:
- Scoping and Traceability: The hierarchical breakdown into Epics, Issues, and Tasks allowed us to define the complete scope of work clearly. This was invaluable for tracing a functional requirement (e.g., "The user wants to view their timetable") back to the specific tasks.
- Workflow Visualization: Using the Boards view, we could quickly see what was in progress and what was completed. This gave us definite closure on requirements. Although we often knew a task's status from meetings, the board provided the single source of truth for the final submission checklist.
- Documentation: For critical logic such as defining the parameters for the two Power Automate flows or detailing the complex Dataverse lookups the work items ensured the logic was captured and available for reference, which was key to troubleshooting many of the integration problems.

#### Challenges and Lessons Learned
Our primary struggles were concentrated at the intersection of low-code development and stringent data source requirements.
##### Main Challenges
1. Dataverse/Power Apps Type Conflicts: The persistent challenge was resolving type incompatibility errors within the galleries and formulas. Specifically:
- Comparing OptionSet (Choice) fields (Role, 'Taking place?') required complex workarounds (e.g., using Text() or Choices().No methods) because Power Apps did not reliably recognize the data type within the collection context.
- The Error, Number conflicts were frequent, forcing us to use stable forms like IsError() or specific Text() comparisons to ensure the logic executed without failing.
2. Geometry and Positioning: The initial setup of the timetable grid required extremely precise mapping of time-based data (Start/End Time) to fixed pixel coordinates (X/Y), often failing due to incorrect variable initialization (e.g., varHourHeight being zero) or incorrect references (Parent.TemplateHeight).
3. Component Binding: Establishing the dynamic visibility of the notification icon required creating a complex Custom Property (IsCancelledAlert) and resolving various circular reference and syntax errors (Property reference isn't valid.) to correctly pass the calculated count to the component.

##### Key Lessons Learned
- Delegate Complex Logic: While Power Apps encourages simplicity, complex relational filtering (especially involving in operators or derived fields) is more stable when explicitly comparing GUIDs or normalizing values (e.g., converting Boolean to Text: "False") before applying CountIf.
- Prioritize Stable References: Avoid relying on dynamic references that are prone to circular logic. Use stable, fixed values (like 60 pixels for an hour height) where possible, or use the With() function for transient calculations.
- The Power of Documentation: Since we faced so many technical conflicts, the initial structure provided by Azure Boards proved valuable. 

#### DevOps vs. Earlier Development Process
This structured DevOps approach differed significantly from earlier, less-structured development processes:
1. Earlier Process (Unstructured): In previous assignments, work was often completed entirely within meetings, and the knowledge of task status was tribal knowledge ("We generally all knew which tasks were done"). If development was divided, there was a higher risk of overlap or missed requirements because we lacked a single reference point.
2. DevOps Process (Structured): Although the formal tooling (Azure Boards) did not drastically change our day-to-day workflow during meetings, its primary difference lay in documentation and accountability. The board served as the comprehensive tool for documenting our logic and confirming the final scope. The ability to trace the implemented Power Automate Flows directly back to the User Story ("Professor wants to cancel a class") provided traceability that was absent in earlier projects. This system ensured that the entire complex solution including the two separate cloud flows was built against verifiable requirements.


---
