# Assignment 4 — Copilot Integration, Monitoring, Testing, and Production Deployment

---

## Copilot Feature

### Description and Purpose
Describe the **Copilot feature** you created in your app using **Microsoft Copilot Studio**.  
Explain what the Copilot is designed to do — for example:
- Helping users navigate the app or retrieve data,
- Automating a repetitive task,
- Providing personalized recommendations or insights.

Clarify **why** this feature adds value for your users or organization.

*Tip:* Use simple, clear examples of user interactions that show how the Copilot improves usability or decision-making.

---

### Knowledge Provided to the Copilot
The purpose of our Copilot agent is to serve as a secure, role-based backend interface for specific logistical operations within our university timetable application. It acts as a central tool for managing scheduling tasks and mandatory student communications, preventing the need for manual database updates.

#### Business Context
- Purpose of the App: 
The primary goal of the application is to create and maintain an optimized, conflict-minimized course timetable and provide real-time updates to all stakeholders (students, staff, and professors).
- Copilot's Role: 
The Copilot handles specific, role-gated transactional actions (e.g., reporting absence, changing room assignment) and authentication. It avoids general, non-data-driven conversations.

#### Structured Data
The Copilot is informed by direct connections to our Dataverse solution components. These tables provide the factual and relational context necessary for the agent's logic.
- Data Sources: 
The agent has read/write access to the following Dataverse tables: Break Time, OpeningHour, Course, Person, Enrollment, and Room.
- Key Columns & Data Used for Logic:
  - Authentication: People table (cre96_email and cre96_password) for user verification.
  - Absence Notification: Course table (to find professor's assignment) and Person table (to find professor's email).
  - Room Change (Staff): Course and Room tables (to find available rooms and update course assignment).
  - Role Determination: Person table (Role Choice field) to determine the user's security level.

#### Conversational Knowledge
The Copilot is restricted to performing actions defined by specific Topics, including: Change room, StudentAbsence, End conversation, and User Authentication. Users are expected to ask direct, actionable questions that trigger these specific workflows.

#### Security and Operational Configuration
We enforced strict security and operational constraints within the agent settings:

##### Security and Permissions
The system implements strict Role Determination by User Authentication:
- The agent first requires the user to authenticate against the People table before any functional topic can be accessed.
- Data Privacy: The agent is strictly prohibited from exposing sensitive data, including passwords, enrollments of other users, or personal emails of other students.

| Role | Access and Limitations | Data Restriction Type | 
|------|------------------------|-----------------------| 
| Student | Can only execute the StudentAbsence workflow. | Limited to personal enrollment and course data. | 
| Professor | Does not have any defined automated actions within the Copilot. | Read-only access to personal status only. | 
| Staff (Scheduler) | Can execute the Change room workflow for any course. | Full access to institutional course and resource data required for management tasks. |

#### Operational Configuration
- Generative AI Orchestration: We ensured that the setting "Use generative AI orchestration for your agent's responses" was Disabled. This is a critical security measure because it prevents the bot from relying on Large Language Model (LLM) processing for conversational flow and forces it to strictly adhere to our predefined topics and authentication flow.
- Web Search: Web search is Disabled. The agent relies exclusively on the internal Dataverse tables for all information and context.
- Agent's Model: The agent uses the GPT-4.1 (default) model for its underlying language understanding capabilities.

---

### Data Connection
Our Copilot connects to the Dataverse backend exclusively through Power Automate Cloud Flows (Actions). This architecture was chosen to ensure that complex data manipulations (like secure authentication and status updates) are handled outside of the conversational interface, enforcing strict security and privacy standards.

#### Connection Strategy
The Copilot triggers a flow whenever it needs to perform a data lookup, update, or execute conditional logic. This is essential for:
1. Gated Access: The flows manage access credentials and enforce role restrictions.
2. Complex Data Handling: The flows handle multi-table lookups (e.g., retrieving a Professor's email by navigating from the Course table) and complex updates (e.g., updating a room lookup field).

#### Implemented Power Automate Flows
We created a suite of seven specific flows to support the agent's full functionality across the three major user roles:
| Flow Name | Purpose & Primary Action | Data Fetched/Updated | Copilot Usage |
|-----------|--------------------------|----------------------|---------------|
| Authenticate_User_And_Get_Role | Security Check & Role Determination: Verifies user credentials against the People table using an OData filter (cre96_email AND cre96_password). | Fetches: cre96_role (Optionset value). | Returns the role text (Professor, Student) via a Switch action to set the global Global.UserRole variable. |
| GetProfessorInfoForAbsence | Lookup Professor Details: Retrieves the assigned professor's contact details for a specific course. | Fetches: Professor's cre96_email and cre96_personname by querying the Courses table and using an Expand Query on the Person lookup. | Provides the necessary email and name inputs for the sending_email flow. |
| sending_email | Automated Communication: Sends a formatted email to the professor regarding a student's absence. | Uses Inputs: professorEmail, courseName, absenceDate, absenceReason, etc.. | Executes the final transactional step of the StudentAbsence topic. | 
| GetCourseRoomInformation | Initial Room Data: Fetches the current room assignments and details for a course. | Fetches: roomName, roomCapacity, and roomType by querying the Courses table and using an Expand Query on the Room lookup field (cre96_Room2). | Displays current resource details in the Change room topic before allowing modification. |
| change_room_agent | Resource Search: Lists all available rooms meeting specific criteria. | Fetches: Room details (cre96_roomname, cre96_capacity, cre96_type) from the Rooms table, filtering by cre96_availability eq true. | Returns a structured array of available rooms for the Staff user to select from. |
| Change room with room update in course | Database Update: Updates the course record with the selected new room. | Updates: The Room (Rooms) lookup field on the specific Course record using the Update a row action. | Confirms the resource assignment transaction is complete in the Change room topic. |
| getUsername | User Detail Retrieval: Retrieves the user's name based on their email. | Fetches: cre96_personname by querying the People table based on the provided email. | Used in the User Authentication topic to personalize messages with the user's name. |

#### Data Usage Summary
Information is consistently fetched from Dataverse using List rows with OData filters or Expand Query for relational data (e.g., retrieving professor emails or room names across lookups). This information is then used by the Copilot to either control the conversation flow (e.g., checking if roomName is blank in the Change room topic) or to populate the final communication (e.g., the email body in the StudentAbsence topic). Updates are handled by the transactional flows using the Update a row action to change resource assignments.

### Include
- Screenshots showing your Copilot in action (e.g., user queries and responses).
- A brief description of your Copilot topic(s) and triggers in Copilot Studio. (If any)
- **Link to your Copilot** (shared from Copilot Studio).

---

## Testing and Monitoring

### Automated Tests
Describe shortly how you used **Power Apps Test Studio** to ensure app quality.  
Include:
- The **names of test suites and test cases**.
- What each test validates (e.g., login, form submission, or Copilot response).
- Any bugs or issues identified during testing.

*Tip:* Tests should focus on core user paths and interactions that affect reliability or data accuracy.

---

### Monitoring and Performance
Use **Power Platform Monitor** to identify performance issues and track user behavior.  
Explain:
- What metrics you reviewed.
- Any bottlenecks found and how they were resolved or improved.

To make documentation consistent for grading:
1. **Save and publish** your test suites in Power Apps Test Studio.
2. **Commit** your Power Apps solution (with the app + tests) to your connected **Azure DevOps** repository.
3. **Commit and push** the latest version to **GitHub**.

Include:
- **Screenshot of your monitoring dashboard or metrics**.
- **Short description** of what you improved based on those insights.
- List test suite and case names.
- Add screenshots from Test Studio showing results.
- Include a note confirming the tests are visible in your GitHub repo (e.g., under `/solutions/<SolutionName>/CanvasApps/.../Tests/`).

---

## Final Version Deployment to Production

### Deployment Process
Describe how you used your **Power Platform pipeline** to deploy the app:
- From **Development → Test → Production** environments.
- Steps taken to run the pipeline.

Verify that the **final version** functions as intended after deployment.

### Include
- Screenshot of the **successful pipeline run** (showing stages).
- Screenshot of the app running in the **production environment**.
- Short description of any issues faced during deployment and how you resolved them.

---

## Reflection

### Reflection and Learning
Write a short reflection discussing:
- How integrating a Copilot changed your app’s **functionality**, **efficiency**, or **user experience**.
- What you learned from **testing and monitoring**, and how it helped you identify improvement opportunities.
- How **automated deployment** and **AI integration** contributed to the **DevOps lifecycle** of your project.


