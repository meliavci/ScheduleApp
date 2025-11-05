# Assignment 3 – DevOps Planning, Pipeline, and Automation

## DevOps Planning (Azure Boards)

### Project Setup
Describe how you created your Azure DevOps (ADO) project and connected it to your GitHub repository.
Include the name of your Power Apps solution and explain how the integration supports version control.

#### Azure DevOps Project Creation and Setup
Our initial step was to establish the centralized hub for our project management and source control linking.

1. Project Creation: Melisa created a new project within our organization's Azure DevOps instance. We chose the project name "ScheduleApp".
2. Member Assignment: Melisa then added all group members to the ADO project team.
3. Permission Management: As the designated manager for the repository, Melisa ensured that everyone had the same necessary permissions to contribute to the code but we faced an issue with the basic role so that Melisa was the only one who had access to the "Repos" section in our Azure project.

#### GitHub Integration and Solution Binding
The core of our version control strategy was linking our local Power Apps development environment to the remote Git repository managed through Azure.

1. Source Control Connection
We initiated the Git connection through two distinct actions:
- Internal Repository Connection: In Azure DevOps, Melisa connected our newly created ADO project to our internal Git repository where the source code for the project would live.
- Power Apps Solution Connection: Within the Power Apps Maker Portal, we navigated to our solution, named "TimescheduleApp", and connected it directly to the designated Git repository branch.

2. Version Control Mechanism
The integration supports version control by formalizing the flow of changes:
- Local Development: All changes made to the components of the "TimescheduleApp" (such as screens, tables, and custom logic) were saved locally within Power Apps Studio.
- Committing Changes: When a developer was ready to share their work, the changes were saved in the Power Apps solution and then we needed to manually commit it to the Azure Repo.
- Synchronization: This commit pushed files representing the solution components (screens, flows, etc.) into the linked Git repository.
- Centralized Management: Since Melisa was the only one who could initially manage the repository, commits were reviewed by the group before being merged into the main development branch. This process, coupled with the permissions given to ensure equal access for contribution, established a reliable system for tracking every iterative change made to the "TimescheduleApp" solution.

This structured approach ensured that all development work, despite the challenges we faced with manual updates at times, was versioned and synchronized across the entire team environment.

**Screenshot:** Azure DevOps project overview with project stats from the right side of the screen.
The Git repository address that you used for your apps. I have created a new folder named "powerapps-solution" in your current repository, where you can use to connect to Power Apps.
<img width="2556" height="1341" alt="image" src="https://github.com/user-attachments/assets/eb5634f0-9643-470b-a9ad-96c8dece5bdf" />
<img width="2559" height="1524" alt="image" src="https://github.com/user-attachments/assets/50d728d5-8dc1-40ad-a60c-1bf81ba0ff07" />


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
| Test logout process | Raphael | To Do | Ensure logout works properly. |
| Implement the logout backend | Raphael | Done | When a user clicks on the logout button their status should change in the database and they should be directed to the log in page. |
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
| Display the generated personalized timetables. | Melisa | Done | Connect the data of each user's generated timetable to their timetable frontend component. |
| Implement backend logic for class cancellation | Melisa | Done | Create database handling for canceled classes. |
| Test notification functionality | Melisa | Doing | Confirm the affected users get notified directly when a change in their timetable happens. |
| Create backend logic when changes happen. | Melisa | Done | Notify affected users about changes in their timetable. |
| Update timetable dynamically after room change | / | To Do | Ensure affected timetable frontend update in real time after editing. |
| Implement backend endpoint to update room details | / | To Do | Check for available rooms for the specific time and type and update the data to the timetable. |
| Add UI option for changing room type | / | To Do | Create a scheduler-only interface to modify the room for a class. |
| Test all user actions for proper handling | Melisa | Doing | Check that every option triggers the correct function. |


**Screenshot:** Azure Boards (To-do, Doing, Done), feel free to add your sprints too.
<img width="2559" height="1397" alt="image" src="https://github.com/user-attachments/assets/f4fbb781-ee82-4d01-86c3-64262ca56c70" />
<img width="1465" height="612" alt="image" src="https://github.com/user-attachments/assets/a544b73a-6ab0-4697-95c1-6a5bd7e899d4" />
<img width="1524" height="873" alt="image" src="https://github.com/user-attachments/assets/fb8cc664-bef5-437a-b212-939efb9d63a4" />


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

We utilized a standard three-tier environment strategy, ensuring clear separation of duties and validation stages before releasing the solution to end-users. The Melisa Avci's Environment served as our primary development sandbox.

| Environment Role | Name | Purpose | Characteristics |
| :--------------- | :--- | ------: |---------------: |
| Development | Melisa Avci's Environment | The source environment where the "TimescheduleApp" was actively built, customized, and linked to the GitHub repository. | Contains unmanaged solutions that allow free editing and debugging. |
| Testing | Testing | Used for validating the solution's functionality (e.g., confirming the flow triggers and timetable logic work) before release. | Receives a managed solution copy to mirror Production stability. |
| Production | Production | The final, live environment where end-users access the functional timetable application. | Includes managed solutions that prevent direct editing and accidental modifications. |


### Pipeline Configuration

**Screenshot(s):** Power Apps pipeline setup (each stage visible).
<img width="2557" height="1396" alt="image" src="https://github.com/user-attachments/assets/514e0db8-2f11-41fb-ba94-bc2106f9c10e" />


**Short Explanation:**

#### What does each stage do?
- Development Stage:
This is where the application and all its components are initially built, configured, and refined. Developers work with unmanaged solutions, allowing full flexibility for design changes, testing, and iteration.
- Testing Stage:
At this point, the solution is deployed as a managed version for evaluation and user testing. The goal is to verify that all features function correctly and that the app behaves as expected before release.
- Production Stage:
This final stage hosts the approved solution used by end users. Since it contains managed solutions, direct editing is disabled to protect stability and ensure a consistent production environment.

#### How is deployment triggered?
Deployments are manually initiated from the Development environment.
The responsible user selects the desired solution, chooses the “Deploy” option, and designates the next environment (Testing or Production).
If required, approval steps can be added so that moving a solution into Production must be authorized by an approver before proceeding.

#### How does this pipeline ensure version control?
Version control is achieved through the use of incremented version numbers for each managed solution deployment.
Every release must have an updated version identifier, ensuring that changes can be traced, previous versions restored if needed, and consistency maintained across environments.
This system prevents overwriting and keeps the deployment history transparent and organized.

### Lessons Learned
Throughout the creation and configuration of our Power Apps pipeline, we identified several key strengths and challenges.

#### What Worked Well
- Version Tracking: The requirement to increment the solution version number before deployment ensured we had a clear, traceable history of changes, allowing us to identify and manage the exact version running in each environment.
- Hosting the pipeline within Melisa Avci’s environment provided a reliable and consistent foundation for deployment and testing activities.

#### Limittations and Challenges
- Repository Synchronization Failure:
A significant limitation was that the local changes to the "TimescheduleApp" solution in the Development environment were not updating the Azure DevOps repository automatically. This required manual commits and was attributed to missing institutional dependencies, creating friction in our continuous integration process.
-  Visibility Restrictions:
A major collaboration issue was that not every group member could see the created pipelines in the Power Apps Maker Portal from Melisa Avci's environment.

---

## Automation with Power Automate

### Flow Description
Explain the purpose of your Power Automate flow.

#### Flow Analysis: Cancel_Course_Notification
##### Flow Description
This instant cloud flow is triggered manually from the Power App (by the professor) to instantly cancel a selected class session in the backend and notify all affected students.
This flow is triggered instantly from the Power App and updates the course status to 'Cancelled'.
##### Short Explanation
- What does the flow automate? The flow automates one step: 1) Updating the course status (Column: “Taking place?”) in the Dataverse Courses table to "No" (Cancelled). 
- Why is it useful for your solution? This flow directly solves the problem of communication delays and ripple effects caused by manual scheduling changes. It ensures that the database reflects the cancellation immediately, fulfilling the expectation for an automatic system.
- How did you test it? The flow was tested by executing the final OnSelect logic of the "Select" button in the Power App. We verified that: 1) The flow ran without error. 2) The target course in the Courses table successfully changed its status (e.g., from 'Yes' to 'No'). 3) The timetable block in the Power App immediately displayed the "Cancelled" icon (due to the Visible property logic) after the screen refresh.

<img width="2559" height="1525" alt="image" src="https://github.com/user-attachments/assets/9c05ca6d-367f-4f30-a910-700772a959f6" />


#### Flow Analysis: Reset_Cancelled_Courses_Daily
##### Flow Description
This scheduled cloud flow runs once daily to clean up the schedule by resetting the status of courses whose cancellation day has passed, ensuring they are automatically available for the next scheduled week.
This flow is triggered on a daily recurrence to check for courses marked as 'No' (Cancelled) whose class day is over, automatically resetting their status to 'Yes' (Scheduled).
##### Short Explanation
- What does the flow automate? The flow automates the status reset of courses. It runs every night (e.g., at 23:45), lists all courses currently marked as "No" (Cancelled), and then checks the course's Weekday against the current day. If the class day has just ended, the flow updates the course's "Taking place?" status back to 'Yes' (Scheduled).
- Why is it useful for your solution? This flow solves the issue of manual schedule adjustments and data hygiene. Without it, a course cancelled one Monday would remain marked as 'No' indefinitely, requiring manual intervention to make it appear on the schedule the following week. The flow ensures the timetable remains accurate and future scheduling is unhindered.
- How did you test it? The flow was tested manually by: 1) Setting a test course's status in Dataverse to 'No'. 2) Manually triggering the scheduled flow. 3) Temporarily adjusting the date and time inside the flow's condition logic to force a comparison with the course's specific Weekday. 4) Verifying that the course's status was successfully updated back to 'Yes' (1).

<img width="2559" height="1394" alt="image" src="https://github.com/user-attachments/assets/330a0983-2b6d-4afe-9fe4-2ae3f5f8a44f" />
<img width="2554" height="1394" alt="image" src="https://github.com/user-attachments/assets/5026e22c-8a26-4190-b7a4-33eefbc1f708" />


---

## Reflection

Reflect on your overall DevOps experience.

#### Azure Boards: Organization and Efficiency
Azure Boards served as our central documentation and visualization tool. While our team often worked collaboratively in meetings and had a flexible assignment style, the platform provided necessary structure:
- Scoping and Traceability: The hierarchical breakdown into Epics, Issues, and Tasks allowed us to define the complete scope of work clearly. This was invaluable for tracing a functional requirement (e.g., "The user wants to view their timetable") back to the specific tasks.
- Workflow Visualization: Using the Boards view, we could quickly see what was in progress and what was completed. This gave us definite closure on requirements. Although we often knew a task's status from meetings, the board provided the single source of truth for the final submission checklist.
- Documentation: For critical logic such as defining the parameters for the two Power Automate flows or detailing the complex Dataverse lookups the work items ensured the logic was captured and available for reference, which was key to troubleshooting many of the integration problems.

#### Pipeline Deployment and Automation 
##### What went well?
1. Reliable Core Functionality
The most significant success was establishing the foundation for a functional Application Lifecycle Management system using Power Platform pipelines.

- Managed Solution Integrity:
We successfully configured the pipeline to deploy the solution artifact sequentially across environments as a Managed Solution. This guarantees that the exact version validated in Testing is moved to Production, which is crucial for maintaining data integrity and system stability.

- Version Control Enforcement:
The requirement to increment the solution version number before deployment enforced a critical best practice. This ensures every release is traceable and helps us manage clear tracking and identification of changes.

2. Efficient Task Automation
We successfully automated two core business requirements using Power Automate Cloud Flows, which directly addressed the problems of manual intervention and communication delays:

- Instant Communication (Cancellation Flow):
We implemented a flow triggered directly from the Power App that instantly updates the course status to 'Cancelled'. This fulfilled the need for immediate, automatic communication and solved the problem of communication delays.

- Automated Data Hygiene (Reset Flow):
We created a scheduled flow that runs daily at a specific time (e.g., 23:45) to automatically reset the status of cancelled courses. This solved the problem of manual data maintenance, ensuring that course availability is correctly restored for the following week.

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
