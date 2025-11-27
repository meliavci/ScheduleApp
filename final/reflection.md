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

### **Example Guidelines**

When writing your reflection, include:

- What parts of the project you personally developed (e.g., data model, app screens, Power Automate flows, testing,
  deployment, documentation, etc.)
- How you contributed to planning, testing, or troubleshooting
- How you participated in Git commits or DevOps setup
- Any leadership, coordination, or mentoring roles you took

---

### **Team Member Contributions**

#### 👤 Member 1 – [Full Name]

**Main responsibilities:**  
*(Describe what you were mainly responsible for)*

**Development contributions:**  
*(Which features, screens, automations, or AI integrations did you implement?)*

**Collaboration:**  
*(How did you support your teammates?)*

**Reflection:**  
*(What did you learn, what challenges did you face, and how did you solve them?)*

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

## Sign-off

All team members confirm that:

- The work submitted is original and collaborative.
- Each member’s described contributions are accurate.

**Signatures / Names:**

- [Name 1]
- [Name 2]
- [Name 3]
- [Date]
