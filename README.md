## Discharge Command Center

A ServiceNow scoped application that coordinates patient discharge across departments, so care teams can see what is blocking a discharge and act on it before it causes a delay.

Built by **Team Ignite** for **HackNow India 2026 (ServiceNow University)**, problem statement HC-01: Patient Discharge Readiness Command Center.

## The problem

Patients who are medically ready to go home often stay for hours or days. Billing, insurance (TPA) approval, pharmacy, transport and follow-up booking sit with different teams, and nobody has one view of what is still pending. This app gives every discharge a single case, splits it into department tasks, tracks progress against SLAs, and escalates anything that gets stuck.

## Features

- **One case per discharge:** when a physician marks a patient medically ready, a flow creates a Discharge Case and six department tasks (Documentation, Billing, TPA/Insurance, Pharmacy, Transportation, Follow-up).
- **Automatic assignment:** a business rule assigns each task to the correct department group based on its task type.
- **Readiness tracking:** a flow recalculates an overall readiness percentage as tasks complete and flags the case when any task is blocked.
- **SLA monitoring:** SLA-based flows send warning and breach notifications to the responsible team.
- **Escalation log:** blocked or overdue tasks create escalation records with automatically stamped escalation and resolution times.
- **Doctor notification:** when every task is complete, an email goes to the patient's allocated doctor.
- **Bed release:** a flow frees the bed once the patient is discharged.
- **Role-based security:** five functional roles (Physician, Department Staff, Discharge Coordinator, Department Lead, Admin) with ACLs, including group-based row-level access so departments see only their own tasks.
- **Patient Service Center portal:** a Service Portal page with Add Patient Details and Book Transportation widgets.
- **Chatbot:** a Virtual Agent topic that answers discharge status questions.
- **Guided forms:** client scripts and UI policies keep data entry clean, for example requiring a blocker note when a task is marked blocked.

## How it works

1. A physician marks a patient **Medically Ready**.
2. **Case Creation & Task Generation** creates the Discharge Case and the six department tasks.
3. A business rule assigns each task to its department group, and the teams are notified.
4. As tasks move to In Progress, Blocked or Completed, **Discharge Readiness** updates the readiness percentage and the blocker flag.
5. SLA flows send warnings and, on breach, log an escalation and notify the team.
6. When all tasks are complete, **Discharge Completeness** marks the case ready and emails the allocated doctor.
7. After discharge, **Bed Release** marks the bed available.

## App at a glance

| Component | Count |
|---|---|
| Flows | 8 |
| Tables | 10 |
| Business rules | 7 |
| Notifications | 7 |
| Client scripts | 5 |
| UI policies | 3 |
| Roles | 16 |
| Access controls (ACLs) | 42 |
| Modules | 10 |

Roles and ACLs include table-level ones that Studio generates automatically, alongside the five functional roles above.

## Tech stack

- ServiceNow scoped application (`x_snc_discharge_0`)
- ServiceNow Studio, Flow Designer, SLA Definitions
- Business rules, client scripts, UI policies, ACL scripts (JavaScript)
- Service Portal and widgets 
- Virtual Agent and NLU Workbench
- GitHub source control integration

## Installation

1. Clone or download this repository.
2. In your ServiceNow instance, open **System Applications → Studio**.
3. Choose **Import From Source Control**.
4. Enter this repository's URL and the `main` branch, then import.
5. Create the five roles' users and department groups, then assign them.

## Repository structure

- `c061500501e303107f447528cba461bb/update`: application records (flows, rules, notifications, scripts)
- `c061500501e303107f447528cba461bb/dictionary`: table and column definitions
- `sn_source_control.properties`: Studio source control configuration

The long folder name is the application's sys_id.

## Team

Team Ignite, Mohan Babu University (6 members).

## Author

**Kiran Tej Reddy Odugu**, Team Lead
[LinkedIn](https://www.linkedin.com/in/kiran-tej-reddy-odugu-451672371)
