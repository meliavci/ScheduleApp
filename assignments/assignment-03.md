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
| Example: Build student registration app | Implement a system where students that register for courses | User login |
| Example: Improve user login | Implement secure login with Dataverse | User authentication, password reset |

| Issue | Description | Related Task(s) |
|-------|--------------|-----------------|
| Example: User wants to reset password | Create new Power Apps screen for password reset | Design form, update Dataverse table |

| Task | Assignee | Status | Notes |
|------|-----------|--------|-------|
| Design reset form | Alice | In Progress | Created new screen component |

**Screenshot:** Azure Boards (To-do, Doing, Done), feel free to add your sprints too.

### Planning and Collaboration
Explain how you used Azure Boards to plan, manage and visualize team work.  
Reflect on how this improved collaboration compared to previous assignments (where tasks may have been less structured).

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

**Example:**
> This flow sends an automatic Teams message when a new customer record is added in Dataverse.

**Flow Diagram or Screenshot:** Flow steps and trigger.

**Short Explanation:**
- What does the flow automate?
- Why is it useful for your solution?
- How did you test it?

---

## Reflection

Reflect on your overall DevOps experience.

- How did **Azure Boards** help organize work and improve efficiency?
- What went well with **pipeline deployment and automation**?
- What were the main challenges and lessons learned?
- How does this DevOps approach differ from your earlier development process?

---
