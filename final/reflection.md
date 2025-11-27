# Final Reflection

## Executive Summary

Our solution is a comprehensive **Business Information System (BIS)** designed to revolutionize university timetable
scheduling. It functions primarily as a **Decision Support System (DSS)** by leveraging data-driven optimization to
generate clash-free timetables, while also handling transactional updates through automation.

**Value of the Final Solution:**
The core value of this solution lies in its ability to transform a static, manual administration task into a dynamic,
automated process. By integrating a Copilot for natural language interaction and Power Automate for backend logic, the
system reduces the cognitive load on staff and provides immediate transparency to students. It shifts the university's
operational capability from reactive maintenance to proactive optimization.

The app directly addresses the inefficiencies, error-prone workflows, and time-consuming nature of manual university
timetable scheduling. Specifically, it eliminates the following critical issues:

* **Course Clashes:** Previously, timetables were frequently unoptimized and prone to course overlaps, which limited
  student flexibility and elective choices. Our system uses structured data validation to prevent these conflicts.
* **Resource Misallocation:** The system solves the issue of limited room availability or rooms being assigned that are
  too small for the enrolled number of students by enforcing capacity constraints during the booking process.
* **Communication Delays:** In the manual process, last-minute changes (such as cancellations or room swaps) often
  failed to reach students and professors in time, causing confusion. Our solution ensures real-time data consistency
  across the board.

### Integration Across Assignments

Each assignment in this course was a sequential step that built the theoretical, functional, and operational foundation
for the final Business Information System (BIS), moving the project from a conceptual analysis to a deployed, managed
solution.

* **Assignment 1 (Theoretical Foundation & Context):** This phase focused on analyzing the **AS-IS** (manual,
  inefficient) scheduling process through Business Process Modeling (BPMN) and Lean analysis. We established the
  project's Problem Statement and defined the **TO-BE** process. Furthermore, we applied the **BIS Classification** (
  identifying the system as a mix of TPS, MIS, and DSS) and utilized the **DIKW Framework** to solidify the theoretical
  need for converting raw data into scheduling wisdom.

* **Assignment 2 (Prototype Development):** In this phase, we mapped the BPMN steps from the TO-BE process into concrete
  app features and a relational data model (Dataverse tables). This resulted in the creation of the **Power Apps
  prototype**, which provided the visual interface for the timetable and enabled core user actions like class
  cancellation.

* **Assignment 3 (DevOps and ALM):** This phase implemented the DevOps practices necessary to manage the application's
  lifecycle. We utilized **Azure Boards** for planning and management and established a **Power Platform Pipeline (
  CI/CD)** for Application Lifecycle Management (ALM). Additionally, we introduced the first layer of automation via
  Power Automate flows to handle logic like course status resets.

* **Assignment 4 (Enhancement and Deployment):** The final assignment integrated the **Copilot** for advanced,
  natural-language automation of administrative tasks (e.g., Student Absence Reporting, Staff Room Change). We performed
  **Testing and Monitoring** using Power Platform Monitor to validate the solution and completed the cycle by deploying
  the final Managed Solution to the **Production environment**.

### Technical & DevOps Practices

Our project utilized a structured Application Lifecycle Management (ALM) system primarily managed through Azure DevOps
and Power Platform Pipelines.

#### Version Control and Branching

We established a strict version control strategy to track granular changes to the low-code files.

* The Power Apps solution, named **"TimescheduleApp,"** was connected directly to the Git repository via **Azure DevOps
  **.
* Changes made in Power Apps Studio were saved locally and then manually committed to the Azure Repo.
* All commits were reviewed before being merged into the main development branch, ensuring a reliable system for
  tracking every iterative change and enabling team collaboration without overwriting work.

#### CI/CD (Continuous Integration/Continuous Deployment)

We established a functional ALM system using **Power Platform Pipelines**.

* **Sequential Deployment:** The pipeline was configured to deploy the solution sequentially across environments: *
  *Development → Testing → Production**.
* **Managed Solutions:** We adhered to the best practice of deploying the solution as a **Managed Solution** to the
  Production environment. This ensures that the exact, validated version from Testing is moved to Production, preventing
  direct editing in the live environment and maintaining system stability.
* **Versioning:** The system enforced the incrementing of the solution version number before every deployment (e.g.,
  1.0.0.1 → 1.0.0.2), making every release identifiable and traceable.

#### Testing and QA

The validation process involved both proactive planning and execution within the Power Platform.

* **Testing Execution:** We performed automated and manual testing using **Power Apps Test Studio** to validate user
  flows (like Login and Cancellation).
* **Validation Focus:** The testing phase was critical for verifying functional correctness, such as the successful
  connection of Power Automate flows to Dataverse and the correct operation of the scheduling logic. It also helped us
  identify platform-specific limitations, such as Test Studio's inability to interact with nested gallery controls.

#### Observability and Monitoring

We utilized **Power Platform Monitor** to analyze the performance of the application.

* **Outcome:** The monitoring analysis did not reveal any decisive bottlenecks (network calls and data retrieval
  performed within acceptable limits). However, it was valuable for understanding the data flow and platform
  limitations.
* **Verification:** The final deployment included a manual verification step to ensure the core user interfaces (e.g.,
  login screen, timetable) loaded and functioned correctly in the live Production environment.

### Business Impact

#### Stakeholders and Users

The solution delivered a significant shift in how the university operates, moving from reactive maintenance to proactive
optimization.

**Primary Users:** Timetable Schedulers/Staff. Their manual workflow is directly replaced by the automated system.
**Other Stakeholders:** Professors and Students.

**Table: Stakeholder Impact Analysis**

| Stakeholder                      | Expectations/Outcomes                                                                            | Impact                                                                                                                                             |
|:---------------------------------|:-------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| **Timetable Schedulers / Staff** | Expected significant reduction in manual work and complex task handling.                         | The role was transformed from a "data entry clerk" to a **"decision manager"**, shifting focus from maintenance to optimization.                   |
| **Professors**                   | Expected respect for their availability and automatic, real-time schedule updates/notifications. | The system automated communication (via Copilot and flows) and provided real-time schedule views, reducing administrative overhead.                |
| **Students**                     | Expected fairness, minimal clashes, and real-time updates for schedule changes.                  | The system's Decision Support System (DSS) capabilities ensure that optimization logic is used to minimize course conflicts and maximize fairness. |

#### Business Outcomes

The application enables several key improvements:

* **Increased Efficiency:** Achieves a significant reduction in the manual work and time spent on scheduling.
* **Shifted Focus:** Transforms the Scheduler's role effectively changing the department's value proposition from simple
  maintenance to strategic optimization.
* **Enhanced Student Experience:** Provides transparency and fairness with minimal collisions (clashes).
* **Strategic Agility:** Allows the system to automatically reshuffle affected classes with minimal ripple effects when
  an issue arises (e.g., a room becomes unavailable), dramatically improving organizational response time.

#### Lessons Learned

* **Copilot Integration Limits:** A key constraint was the institutional inability to publish the bot due to tenant
  restrictions. This prevented a seamless, direct integration with the live Power App, forcing the team to use a
  workaround (external link) rather than an embedded experience.
* **Complex Logic Delegation:** We learned that complex relational filtering (e.g., comparing derived fields or option
  sets) is more stable and reliable when the logic is delegated to explicit comparisons (like GUIDs) or normalized
  values, rather than attempting complex in-app filtering formulas.
* **Value of Documentation:** The initial structured documentation provided by **Azure Boards** proved invaluable. It
  allowed us to trace functional requirements back to specific technical tasks, which was essential when troubleshooting
  technical conflicts and complex logic later in the project.

---

## Future Work

If we had more time, we would implement the following features to move from a "Minimum Viable Product" to a fully
autonomous system:

1. **Algorithmic Generation Engine:** Currently, the system manages existing timetables. The next logical step is to
   implement the actual optimization algorithm (e.g., using Azure Functions or Logic Apps) that *generates* the
   clash-free master schedule from scratch one week before the semester starts, based on constraints.
2. **Integrated SSO Authentication (Feide):** We would replace our manual login workaround with true Single Sign-On (
   SSO) using a provider like **Feide** or Azure AD. This would allow users to log in effortlessly with their existing
   school accounts.
3. **Full Copilot Integration:** We would resolve the institutional tenant restrictions to publish the Copilot directly
   into the Power App. This would remove the need for the external website workaround and allow the bot to automatically
   recognize the logged-in user context.
4. **Automated Push Notifications:** While we started the backend logic for notifications, the front-end integration is
   currently a mockup. We would fully implement the Power Automate flow to send instant push notifications to students'
   mobile devices whenever a class is cancelled or moved.

---

## Detailed Teamwork Reflection

### **Team Member Contributions**

---

#### Melisa Avci

**Main responsibilities:**  
I acted as the **Project Lead and Lead Developer**, taking full ownership of the organization, execution, and final delivery of the project. My role went far beyond standard contribution; I was the central hub for all development, infrastructure, and documentation.

*   **Group Coordination & Execution:** In our physical meetings, I was the **active operator**. I connected my laptop to the group room TV and performed the actual development work in real-time. While my teammates watched and provided feedback, I was the one translating that feedback into code, logic, and design immediately.
*   **Task Management:** I mostly defined the project scope and assigned tasks to members. I actively tried to animate and motivate the group to contribute, but due to the gap in technical competence, I often had to take over their assigned tasks to ensure the solution worked.
*   **Infrastructure Owner:** I set up and managed the entire DevOps environment (Azure DevOps, GitHub, Power Platform Environment). I manually handled **every single Git commit, sync, and push** for the entire team throughout the semester in our repository.
*   **Final Delivery:** I took responsibility for the final polish of all deliverables. This included formatting the entire written report, finalizing the templates, integrating the professor's feedback, and even cutting and editing the final submission video.

**Development contributions:**  

*   **Assignment 1 (Analysis & Design):**
    *   I participated creating the **BPMN diagrams** to model the TO-BE process.
    *   I developed the **Ishikawa (Fishbone)** analysis to identify the root causes of scheduling inefficiencies.

*   **Assignment 2 (Data & App Architecture):**
    *   **Dataverse Architecture:** I designed and created the entire Dataverse schema from scratch. This involved creating the tables for e.g. `Course`, `Person`, `Room`, `Enrollment`, `OpeningHour`, and `BreakTime`. I input all the dummy data and defined the complex relationships (e.g., Many-to-Many for Enrollments), personally resolving specific "Cascade All" error conflicts that stopped other team members.
    *   **Backend Logic:** I implemented the complete backend logic for the **Login screen**, using complex `ClearCollect` sequences to fetch user-specific enrollments (`colUserEnrollments`) and courses.
    *   **Timetable Engine:** I built the core logic for the **Timetable screen**. This was the most technically difficult part, requiring me to write complex mathematical formulas to calculate dynamic X/Y coordinates for course blocks based on `Weekday` and `StartTime` so they would appear in the correct grid slots.
    *   **UI & Navigation:** I overhauled the entire UI to ensure consistency, fixing layout issues and implementing the navigation logic across all screens. I also built the visual status indicators, such as the red "X" icon for cancelled courses, using `CountRows` and text-conversion workarounds to handle Boolean logic failures.

*   **Assignment 3 (DevOps & Automation):**
    *   **Infrastructure:** I set up the "ScheduleApp" project in Azure DevOps, created the GitHub repository, and established the connection between the two.
    *   **Pipelines:** I configured the **Power Platform Pipelines** for ALM, managing the manual deployment from my Development Environment to Testing and finally to Production.
    *   **Power Automate Implementation:**
        *   **`Cancel_Course_Notification`:** I built this instant flow to update the Dataverse status to 'Cancelled'. I personally debugged and resolved specific JSON parsing errors (`TriggerBody`) that were preventing the flow from reading the CourseID.
        *   **`Reset_Cancelled_Courses_Daily`:** I created this scheduled flow to reset course status overnight. I implemented the necessary OData filter logic (`_cre96_takingplace_value eq 0`) and timezone conversions to compare the course weekday with the current day.

*   **Assignment 4 (Copilot & QA):**
    *   **Bot Creation & Architecture:** I defined the entire scope and architecture of the "Scheduler" bot. This involved defining the specific **Topics**, configuring the **Knowledge** base (connecting it to the specific Dataverse tables I designed), and setting the system definitions to ensure it behaved as a role-gated assistant rather than a generic chat bot.
    *   **Copilot Logic:** I created the **"User Authentication"** topic and the logic to force this topic to run at the start of every conversation by redirecting the System Greeting. I implemented the **`Authenticate_User_And_Get_Role`** flow, including the OData filter to match email/password and the Switch logic to return the text-based User Role.
    *   **Agent Configuration:** I handled the agent configuration, ensuring Generative AI was disabled to force deterministic behavior and defining strict data privacy rules.
    *   **Testing & Monitoring:** I set up and ran the test suites in **Test Studio** (e.g., `loginAsStudent`, `cancelClassAsProf`), identifying critical bugs like the inability to select buttons in nested galleries. I also used **Power Platform Monitor** to analyze network calls (`getRows`, `patchRow`) to ensure app stability.

**Collaboration:**  
My collaboration experience was defined by a need to bridge the gap between the group's output and the project requirements.
*   **Animation & Integration:** I constantly tried to integrate all members by assigning them tasks and encouraging participation in meetings. However, when members struggled with technical tasks or delivered incomplete work, I stepped in to fix it.
*   **Workload Distribution:** To meet our deadlines, I performed a significant amount of work alone at home. This involved rewriting backend logic that others couldn't get to work and fixing UI alignment issues.
*   **Documentation Lead:** I wrote the core content for the report templates. While I asked others to contribute sections, I often had to rewrite contributions to ensure they were accurate, professional, and formatted correctly in Markdown. I was the one who managed the final compilation of the report.

**Reflection:**  
*   **Technical Mastery:** This project forced me to become an expert in the Power Platform ecosystem. I learned how to resolve high-level type conflict errors (Error, Number, OptionSetValue) in Power Fx and how to architect a full ALM pipeline from scratch.
*   **Leadership & Resilience:** The biggest challenge I faced was the uneven division of labor. Acting as the leader for the repository, program setups and even the group itself and the primary developer for every complex feature was incredibly stressful. However, it taught me that successful delivery sometimes requires taking on the burden of execution—coding the logic, writing the report, and reworking tasks—while still trying to keep the team engaged. I learned how to drive a project forward through sheer determination, ensuring that despite the team's varying skill levels, we delivered a high-quality, distinction-level product.

---

#### Aleksandra Wos

**Main responsibilities:**  
*   Giving inputs to tasks in the assignments where I thought they were needed.
*   Doing the tasks in the assignment that were given to me.

**Development contributions:**  

*   **In Assignment 1:**
    *   Identified the type of organizational change text.
    *   Wrote some parts of the stakeholders text.
    *   BPMN modeling together with the rest of the team.

*   **In Assignment 2:**
    *   Identified most of the key requirements from BPMN in our Google Doc before the text was rewritten in the GitHub template; the rest of the team and I did the mapping.
    *   Gave input to Melisa when she was doing the Copilot plan designer.
    *   Developed the Power Apps Prototype notifications interface and component low code with help from Raphael.

*   **In Assignment 3:**
    *   Defined the tasks in Azure work items and added them to the GitHub template table.

*   **In Assignment 4:**
    *   For the Copilot Studio agent, I created a new Power Automate flow and worked on parts of the "Change Room" topic that utilized it. The change room agent flow checks room availability. After I created it, Raphael made formatting changes so that the agent response was readable. This was done the next day after a meeting with the whole group, where just Raphael and I met up and worked on the Copilot agent for 4.5 hours.
    *   Gave input on the instructions text in our agent.

For each assignment, the whole team gave input to the "lessons learned" part, as well as most of the text for the assignments. I don't think the contribution part really shows the scope purely from the tasks that I did because of how we worked together as a team. For most of the work, we met up physically in a group room at the university, multiple times a week, to work for multiple hours at a time. In these meetings, all team members had the chance to participate and give inputs on how we wanted to do the assignments and what text to write for the submissions.

The parts I changed after the feedback:
*   **Assignment 1:** Ishikawa diagram (Melisa helped) and helped with BPMN.
*   **Assignment 2:** Introduction to sections 8.3.2 and 8.3.3, and I also did the executive summary.

**Collaboration:**  
*   Gave ideas for the assignment tasks and collaborated where possible, but with the programs used in this course, this was difficult at every stage because they are not catered to collaboration.
*   Therefore, as I mentioned previously, most of the work was done with the whole team in physical meetings at the university. Melisa has done the most work, spending time outside the meetings to complete tasks that needed to be done. However, some tasks look like she did them by herself because we were using her environment in Power Apps, her Azure, and her GitHub. I and other team members participated in the physical meetings to do the work; we used the TV in the group room to see Melisa's screen, and from there I/we gave feedback, inputs, and ideas while the changes were made on Melisa's laptop.
*   Tried to be understanding of Shehab when he didn't understand the assignments and tried to explain things so he would understand. There were two distinct meetings where he didn't give any inputs at all, but after the whole team spoke to him and he explained he had personal family issues going on, his communication from that point on got better in my opinion. The way I supported him was by trying to understand his perspective.

**Reflection:**  
*   **What did you learn, what challenges did you face, and how did you solve them?**
    For testing in Assignment 3, we found out that only one person can do tests at a time because co-authoring gets turned off when one person starts the test. Therefore, we had to do the tests together even though we originally planned for each team member to do their own test individually.
*   **How you contributed to planning, testing, or troubleshooting:**
    As a team, we always planned what work we were going to do for our in-person meetings.
*   **How you participated in Git commits:**
    Suggested changes to text in GitHub.
*   **Any leadership, coordination, or mentoring roles you took:**
    I took on the mentoring role when I thought my ideas made more sense than what my team members suggested.

---

#### Shehab Wael Abozied Abdelhamed

**Main responsibilities:**
In this project, I mainly worked on the Profile Page in Power Apps and helped my team with the project templates, since we often completed them together. My focus was on supporting the front-end and helping where needed.

**Development contributions:**
*   Built the basic layout of the Profile Page.
*   Connected some fields to Dataverse with the help of my teammates.
*   Filled in some data in a few Dataverse tables to support testing.
*   Helped with testing to make sure the screens worked correctly.

**Collaboration:**
*   Worked with the team on templates and documentation.
*   Coordinated with teammates so my page matched their data structure.
*   Helped with small fixes and testing when needed.

**Reflection:**
This project helped me learn more about Power Apps, UI basics, and data binding. I couldn’t attend all meetings, but I always tried to catch up and finish my part. As a team, we communicated well, discussed issues together, and even did online meetings when needed to solve problems. Using AI tools also helped me understand errors and learn faster. Overall, this project improved my teamwork and technical skills.

---

#### Raphael Tam-Dao

**Main responsibilities:**
Our group worked very collaboratively, completing most tasks together in joint work sessions. Although we did not begin with fixed roles, our responsibilities shifted whenever tasks were divided. During those moments, my main responsibility became the tasks assigned specifically to me, and I took ownership of completing them while still supporting the entire group. Overall, my role combined shared teamwork with individual responsibility when we split the workload.

**Development contributions:**

*   **Power Apps:**
    *   Developed the frontend of the login screen.
    *   Implemented the logout button and its corresponding backend logic.
    *   Developed the backend logic for the navbar component, enabling navigation between core screens.
    *   Implemented the backend logic for retrieving user profile data such as name, email, and role.

*   **Copilot Studio (Topics & Automations):**
    *   I created and implemented several Copilot topics and Power Automate flows.
    *   **Topic: Change Room**
        *   *GetCourseRoomInformation* – Retrieved room name, type, and capacity for the selected course.
        *   *ChangeRoomAgent* – Retrieved all available rooms, concatenated and formatted them, and displayed them through the chatbot.
        *   *Change room with room update in course* – Looked up the room to be changed, updated the course with the new room, and set the chosen room to unavailable.
    *   **Topic: Student Absence**
        *   *Get Professor Info for Absence* – Retrieved the professor’s email and name to support absence notifications.

*   **Testing:**
    *   Testing was integrated into every implementation step.
    *   I tested all Copilot flows to confirm correct row filtering, formatting, data retrieval, and Dataverse updates.
    *   I tested backend navigation logic and component behavior in Power Apps.
    *   I verified the logout functionality and profile data loading.
    *   I participated in group test sessions and test suite creation.

**Collaboration:**
*   We collaborated very closely throughout the project. We planned together, created the automated test suites together, and jointly troubleshot UI issues, flow errors, and Dataverse-related problems.
*   We all participated in the Git commits and Azure DevOps setup. Since DevOps setup and Git file management had to be done through one account (Melisa’s), she shared her screen while we all worked through the steps together in the same room—discussing decisions, writing commits, and verifying changes as a team.
*   We used a shared Google Docs document where everyone contributed to the written report. Melisa then transferred the final text into the Git repository file since only one person could commit it.
*   When tasks were divided, I helped teammates who encountered technical difficulties in Power Apps, Power Automate, or Copilot topics, and we resolved the problems together.

**Reflection:**
This project broadened both my technical skills and my ability to collaborate effectively. I improved at communicating and working with teammates who had different personalities and working styles than I was used to. While this occasionally led to challenges, we solved them through open discussion and mutual support.

Technically, I learned how to work with:
*   Power Apps (Power FX)
*   Power Automate
*   Copilot Studio
*   Dataverse
*   Azure DevOps
*   Camunda (especially BPMN modeling, which was difficult at first but ultimately manageable)

Power Automate was extremely strict with formatting, row listing, and updates, which made debugging frustrating. Power FX was also unfamiliar, but with research and practice, I became more comfortable using it. Working on BPMN diagrams in Camunda was another difficult challenge, but I gained a solid understanding of how to model processes properly. Co-authoring in Power Apps also caused issues—especially when multiple people edited the same screen—but we learned to coordinate better and avoided major conflicts. Despite starting with no prior experience in these tools, I adapted, completed my features, and contributed in multiple areas across the project.

---

#### Victor Wilhelmsen

**Main responsibilities:**
I took responsibility for a few technical tasks, as well as assisting the team whenever needed. I also helped troubleshoot issues along the way so that the workflow stayed consistent for the whole team. I personally think that I could have done more alone, but it might not have met the quality standards the group desired.

**Development contributions:**  
I designed the Ui for the power apps navbar, as well as the navigation logic, with help from others from the team. I also contributed on the flows as help, some of the ai as help, and on the Camunda BPMN. I also assisted in reviewing pipeline steps and ensuring that the deployment flow followed DevOps practices.

We did the documentation and testing together in meetings. We figured out how to do it by ourselves, then in the meeting we did all the tests and the documentation together.
We also did the assignment templates together as meetings at the end of our working process for the assignments.

**Collaboration:**  
Our team had physical meetings every week, to ensure quality. This means that during those meetings we discussed our possibilities until we would land one, then do that one. When a problem appeared, the team would try to find a solution during these meetings.
We did have some difficulties, especially in the beginning, with communication. Over the course of the semester, I personally feel like this got better, and the group was ok. We also tried to have some meetings online. This did not really work that well, so we eventually stopped and only had physical meetings.
We should have maybe distributed more tasks, instead of doing it in the meetings. However, we did get to have discussions which helped the entire process.

**Reflection:**  
Throughout the project, I learned more about how DevOps tools fit together, including how pipelines, automation, and version control work in practice. Some of the difficulties we had were problems with authoring and figuring out how everyone could edit, especially in power apps. We also had some problems dealing with environment inconsistencies, but we were able to work through them with research and assistance from the team.

---

## Sign-off

All team members confirm that:

- The work submitted is original and collaborative.
- Each member’s described contributions are accurate.

**Signatures / Names:**

- Melisa Avci
- Victor Wilhelmsen
- Aleksandra Wos
- Raphael Tam-Dao
- Shehab Wael Abozied Abdelhamed
- 27.11.2025
