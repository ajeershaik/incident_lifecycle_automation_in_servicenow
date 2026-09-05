# Incident Lifecycle Automation in ServiceNow

## 📌 Project Overview

**Incident Lifecycle Automation in ServiceNow** is a ServiceNow-based project designed to automate and standardize the complete Incident Management lifecycle.

The solution enables Service Desk agents to **create, classify, investigate, escalate, resolve, and track incidents** while integrating:

* Incident Management
* Knowledge Management
* Agent Assist
* Change Management
* SLA Management
* Configuration Management
* Service Management
* Child Incident Management
* Related Records

The primary objective is to establish a structured and traceable incident-handling process from initial reporting through final resolution and knowledge creation.

---

## ❗ Problem Statement

Organizations regularly encounter IT-related incidents such as:

* Network failures
* VPN authentication problems
* Hardware issues
* Application failures

When these incidents are handled manually or inconsistently, organizations may face:

* Incorrect or incomplete incident classification
* Delayed assignment to the appropriate support team
* Difficulty finding existing solutions
* Poor visibility into incident progress
* Lack of proper escalation mechanisms
* Manual tracking of related change requests
* Difficulty tracking recurring or related incidents
* Incomplete cause and resolution documentation
* Poor SLA compliance

Therefore, an integrated and standardized Incident Management solution is required.

---

## 💡 Proposed Solution

The proposed ServiceNow solution automates the incident lifecycle by providing:

1. Incident creation through Service Operations Workspace
2. Standardized incident classification
3. Knowledge Article recommendations through Agent Assist
4. Assignment and escalation to appropriate support groups
5. Emergency Change Request integration
6. Child Incident creation
7. Cause and resolution documentation
8. Knowledge Article creation from resolved incidents
9. SLA and related-record tracking
10. Multi-team collaboration and incident visibility

---

# 🎯 Project Goals

The major goals of the project are:

1. Standardize incident creation and classification
2. Reduce incident resolution time
3. Improve incident assignment and escalation
4. Reuse existing knowledge for faster troubleshooting
5. Integrate Incident and Change Management
6. Track recurring issues using Child Incidents
7. Maintain proper cause and resolution information
8. Convert useful incident resolutions into Knowledge Articles
9. Improve SLA compliance and service visibility
10. Provide an end-to-end incident lifecycle

---

# 📋 Requirements

## Business Requirements

| Requirement           | Description                                                                          |
| --------------------- | ------------------------------------------------------------------------------------ |
| Incident Creation     | Service Desk agents should be able to create incidents                               |
| Classification        | Incidents should contain category, subcategory, urgency, service, and CI information |
| Knowledge Integration | Agents should be able to search and attach relevant Knowledge Articles               |
| Assignment            | Incidents should be assigned to appropriate support groups                           |
| Escalation            | Level 2 teams should be able to investigate and resolve incidents                    |
| Change Integration    | Emergency changes should be associated with incidents                                |
| Child Incidents       | Related or recurring issues should be tracked through Child Incidents                |
| Resolution            | Cause, resolution code, and resolution notes should be documented                    |
| Knowledge Creation    | Resolved incidents should be converted into Knowledge Articles where appropriate     |
| SLA Tracking          | SLA information should be visible throughout the incident lifecycle                  |

---

# ⚙️ Functional Requirements

### FR-01: Service Creation

Create the following service:

* **Service:** Remote Access
* **Operational Status:** Operational

### FR-02: Service Offering Creation

Create a service offering under Remote Access:

* **Service Offering:** Corporate VPN
* **Parent Service:** Remote Access
* **Operational Status:** Operational

### FR-03: Incident Creation

The incident should support:

* Short Description
* Caller
* Assignment Group
* Description
* Channel
* Category
* Subcategory
* Urgency
* Service
* Service Offering
* Configuration Item

### FR-04: Incident Classification

Example classification:

```text
Category: Network
Subcategory: VPN
Urgency: 2 – Medium
Service: Remote Access
Service Offering: Corporate VPN
Configuration Item: ThinkStationS20
```

### FR-05: Knowledge Integration

Agent Assist should recommend relevant Knowledge Articles based on the incident description.

The agent should be able to:

* View recommended articles
* Open an article
* Mark an article as Helpful
* Attach the article to the incident
* Add comments regarding the article

### FR-06: Watch List and Work Notes

Users should be able to monitor incident progress through:

* Watch List
* Work Notes List

### FR-07: Reassignment

Incidents should be reassigned from Service Desk to the appropriate Level 2 support group.

Example:

```text
Service Desk → Network
```

### FR-08: Investigation

The Level 2 Network team should be able to:

* View incident details
* View Knowledge Articles
* Review activity
* View SLA information
* Take ownership of the incident

### FR-09: Change Integration

When a change is required to resolve an incident:

```text
Incident State: On Hold
On Hold Reason: Awaiting Change
```

An Emergency Change Request should then be created and associated with the incident.

### FR-10: Child Incident

The system should support Child Incident creation for recurring or related issues.

The Child Incident must remain linked to its Parent Incident.

### FR-11: Cause Documentation

The probable cause of the incident should be documented.

Example:

```text
PowerEdge service was suspended and required restart.
```

### FR-12: Resolution Documentation

The system should record:

* Resolution Code
* Resolution Notes

Example:

```text
Resolution Code:
Workaround provided

Resolution Notes:
Restarted VPN-SRV-02 service as per emergency change request.
```

### FR-13: Knowledge Article Creation

After resolving the incident, a reusable Knowledge Article should be created.

```text
Knowledge Base: IT
Template: Standard
```

### FR-14: SLA Tracking

Applicable SLA information should be visible through the incident's related records.

---

# 🏗️ Solution Architecture

The solution uses ServiceNow's integrated modules to manage the complete Incident Management lifecycle.

## Service Structure

```text
Remote Access
     │
     └── Corporate VPN
```

Where:

* **Remote Access** → Parent Service
* **Corporate VPN** → Service Offering

## ServiceNow Capabilities Used

The project integrates:

* Incident Management
* Knowledge Management
* Agent Assist
* Change Management
* Service Management
* Configuration Management
* SLA Management
* Related Lists
* Child Incidents

---

# 🔄 Incident Lifecycle

The overall incident process follows this sequence:

```text
Service Configuration
        ↓
Incident Creation
        ↓
Incident Classification
        ↓
Knowledge Assistance
        ↓
Collaboration & Escalation
        ↓
Level 2 Investigation
        ↓
Emergency Change
        ↓
Child Incident
        ↓
Cause Documentation
        ↓
Resolution
        ↓
Knowledge Article Creation
        ↓
Testing & Validation
```

This lifecycle provides a structured process from incident reporting through resolution and knowledge reuse.

---

# 🗺️ Project Roadmap

The project is divided into **15 milestones**:

| Milestone | Activity                 |
| --------- | ------------------------ |
| 01        | Create Service           |
| 02        | Create Service Offering  |
| 03        | Create Incident          |
| 04        | Classify Incident        |
| 05        | Integrate Knowledge      |
| 06        | Update Watch List        |
| 07        | Reassign Incident        |
| 08        | Level 2 Investigation    |
| 09        | Create Emergency Change  |
| 10        | Create Child Incident    |
| 11        | Add Cause                |
| 12        | Add Resolution           |
| 13        | Create Knowledge Article |
| 14        | Final Validation         |
| 15        | Testing and Deployment   |

---

# 🛠️ Implementation

## Phase A — Service Configuration

### Step 1: Create Service

Navigate to:

```text
All → cmdb_ci_service.list → New
```

Create:

```text
Name: Remote Access
Operational Status: Operational
```

### Step 2: Create Service Offering

Navigate to:

```text
All → service_offering.list → New
```

Create:

```text
Name: Corporate VPN
Parent: Remote Access
Operational Status: Operational
```

**Deliverable:** Remote Access service with Corporate VPN service offering.

---

## Phase B — Incident Management

Navigate to:

```text
Service Operations Workspace
→ List
→ Incidents
→ Open
→ New
```

Create the incident with:

```text
Short Description:
Unable to connect to Corporate VPN from home office

Caller:
Michael Hoefer

Assignment Group:
Service Desk
```

Save the incident.

### Incident Classification

Update the incident:

```text
Description:
Michael advised he was able to connect yesterday evening,
but this morning received an authentication error.
The Internet works fine.

Channel: Phone
Category: Network
Subcategory: VPN
Urgency: 2 – Medium
Service: Remote Access
Service Offering: Corporate VPN
Configuration Item: ThinkStationS20
```

Add the work note:

```text
Classified and assigned incident.
```

Then select **Assign to me** and save.

---

# 📚 Phase C — Knowledge Management

Open **Agent Assist** from the right-side panel.

Perform the following:

1. Verify recommended Knowledge Articles
2. Open a relevant article
3. Select the three-dot menu
4. Mark the article as Helpful
5. Select Attach Article
6. Add the comment:

```text
Follow the steps and resolve the incident.
```

7. Attach the article
8. Return to the incident
9. Verify the article in the Activity log

---

# 👥 Phase D — Collaboration & Escalation

## Watch List

Add:

```text
Watch List:
Samantha Bordwell

Work Notes List:
Beth Anglin
```

This allows stakeholders to monitor incident updates.

## Incident Reassignment

Change:

```text
Assignment Group → Network
```

Verify that the **Assigned To** field is cleared automatically when the assignment group changes.

---

# 🔍 Phase E — Level 2 Investigation

Impersonate the Level 2 Network technician.

Navigate to:

```text
Service Operations Workspace
→ Incidents
→ Open
```

Open the VPN incident and select **Assign to me**.

Verify:

* Incident description is available
* Knowledge Articles are available
* SLA information is visible
* Task SLAs appear under Related Records
* Incident information is accessible to the Network team

---

# 🔄 Phase F — Emergency Change Integration

Update the Configuration Item as required.

Set:

```text
State: On Hold
On Hold Reason: Awaiting Change
```

Create or associate the required **Emergency Change Request**.

The Change Request maintains traceability between the incident and the technical fix.

---

# 🔗 Phase G — Child Incident Management

Navigate to:

```text
Related Records
→ Child Incidents
→ New
```

Create:

```text
Short Description:
Unable to connect to Corporate VPN

Caller:
Any available user

Description:
User receiving VPN authentication failure error
```

Save the Child Incident and record its incident number.

Return to the Parent Incident and verify the Child Incident under **Related Records**.

---

# 📝 Phase H — Cause & Resolution

## Cause Documentation

From the Overview tab, select **Add Cause**.

Enter:

```text
Probable Cause:
PowerEdge service was suspended and required restart.
```

Save the cause information.

## Resolution Documentation

Select **Add Resolution**.

Enter:

```text
Resolution Code:
Workaround provided

Resolution Notes:
Restarted VPN-SRV-02 service as per emergency change request.
```

Save the resolution and select **Resolve**.

---

# 📖 Phase I — Knowledge Article Creation

After resolving the incident, select **Create Knowledge**.

Configure:

```text
Knowledge Base: IT
Article Template: Standard
```

Select **Next**.

Verify the incident and resolution information, then save the Knowledge Article.

Finally, navigate to:

```text
Related Records → Knowledge
```

Verify that the newly created Knowledge Article is linked to the incident.

---

# 🧪 Testing & Validation

The implementation should be tested against the complete Incident Management lifecycle.

| Test Case             | Expected Result                                                                           |
| --------------------- | ----------------------------------------------------------------------------------------- |
| Incident Creation     | Incident is successfully created with caller and short description                        |
| Classification        | Category, subcategory, urgency, service, service offering, and CI are correctly populated |
| Knowledge Integration | Relevant Knowledge Articles appear in Agent Assist and can be attached                    |
| Reassignment          | Incident moves from Service Desk to Network Support                                       |
| SLA                   | Applicable SLA is visible under Task SLAs                                                 |
| Change Integration    | Emergency Change Request is linked to the incident                                        |
| Child Incident        | Child Incident is created and displayed under the Parent Incident                         |
| Resolution            | Cause and resolution information are recorded and incident moves to Resolved              |
| Knowledge Creation    | Knowledge Article is created from the resolved incident and linked to it                  |

---

# ✅ Final Validation Checklist

Before completing the project, verify:

* [ ] Parent Incident is **Resolved**
* [ ] Child Incident is **Resolved**
* [ ] Incident Activity contains resolution information
* [ ] Change Request is linked
* [ ] Knowledge Article is created
* [ ] Knowledge Article is linked to the incident
* [ ] SLA tracking is visible
* [ ] Assignment and reassignment work correctly
* [ ] Incident classification is accurate
* [ ] Watch List is populated
* [ ] Work Notes List is populated
* [ ] Parent–Child Incident relationship is maintained
* [ ] Complete incident history is available

---

# 📦 Project Deliverables

| Phase                      | Deliverable                                      |
| -------------------------- | ------------------------------------------------ |
| Service Configuration      | Remote Access Service and Corporate VPN Offering |
| Incident Management        | Created and classified VPN Incident              |
| Knowledge Management       | Knowledge Article attached to Incident           |
| Collaboration & Escalation | Incident assigned to Level 2 Network Support     |
| Change Management          | Emergency Change linked to Incident              |
| Child Incident Management  | Parent–Child Incident relationship               |
| Resolution                 | Cause and Resolution details                     |
| Knowledge Creation         | New IT Knowledge Article                         |
| Final Phase                | Validated and tested project                     |

---

# 🎯 Expected Outcome

At the completion of the project, **Incident Lifecycle Automation in ServiceNow** demonstrates a complete and structured Incident Management process covering:

```text
Service Configuration
        ↓
Incident Creation
        ↓
Classification
        ↓
Knowledge Assistance
        ↓
Escalation
        ↓
Level 2 Investigation
        ↓
Change Management
        ↓
Child Incident Management
        ↓
Cause & Resolution
        ↓
Knowledge Creation
        ↓
Validation
```

The final solution provides a structured, traceable, and integrated approach to handling incidents throughout their lifecycle.

---

## 📌 Project Status

**Project:** Incident Lifecycle Automation in ServiceNow
**Platform:** ServiceNow
**Domain:** IT Service Management / Incident Management
**Primary Workflow:** Incident → Investigation → Change → Resolution → Knowledge

**Status:** Testing and Validation
