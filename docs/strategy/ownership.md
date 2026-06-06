# Content Ownership Model

## 1. Ownership Philosophy

The Enterprise Content Ownership Model eliminates ambiguity regarding who is responsible for the accuracy, readability, and maintenance of infrastructure documentation.

In a high-stakes engineering environment, documentation cannot be a secondary, unassigned task. This model enforces a strict bifurcation of responsibility: **Subject Matter Experts (SMEs) own the technical truth**, while the **Documentation Team owns the information architecture, usability, and governance.**

---

### Objectives

- **Eradicate Orphaned Content:** Ensure every single page in the repository has a dedicated human or team accountable for its upkeep.
- **Streamline SME Workloads:** Remove the burden of formatting, taxonomy, and Markdown syntax from civil and systems engineers.
- **Enforce Accountability:** Tie documentation review cycles directly to engineering KPIs and project deliverables.

---

### Core Roles and Responsibilities

#### 1. The Subject Matter Expert (SME)

_Typically: Lead Civil Engineers, Systems Architects, HSEQ Officers._

- **Accountability:** Absolute technical accuracy and compliance with physical engineering reality.
- **Responsibilities:** \* Provide raw technical data, parameter tables, and process logic.
  - Review and approve drafted PRs (Pull Requests) within the 5-day SLA.
  - Respond to automated Jira review tickets when a document nears expiration.
- **What they DO NOT do:** Formatting, writing CSS, managing Git merge conflicts, or worrying about taxonomy tags.

#### 2. The Technical Writer

_Typically: Embedded members of the Documentation Architecture team._

- **Accountability:** Readability, findability, and adherence to enterprise style standards.
- **Responsibilities:**
  - Interview SMEs to extract tacit knowledge.
  - Draft procedures into standard Markdown using the approved Topic-Based Architecture.
  - Apply correct metadata (YAML) and taxonomy tags.
  - Manage the Git CI/CD pipeline and resolve merge conflicts.

#### 3. The Document Owner (Team Level)

Individuals leave the company; teams remain. Therefore, the `author` field in the document metadata must always reflect a **Role or Team**, never a specific person.

- **Example:** Use `Author: Rail Signaling Team` instead of `Author: John Smith`.
- If a Jira review ticket is generated, it is routed to the Team Lead's queue, preventing orphaned documents when an individual transitions.

---

### The RACI Ownership Matrix

This matrix governs the interaction during a standard Engineering Change Request (ECR) documentation update.

| Task / Phase                         | SME / Lead Engineer | Technical Writer | Doc Architect | HSEQ Officer |
| :----------------------------------- | :-----------------: | :--------------: | :-----------: | :----------: |
| **1. Identify Knowledge Gap**        |        **R**        |        C         |       I       |      I       |
| **2. Extract Raw Data (Confluence)** |        **R**        |      **R**       |       I       |      C       |
| **3. Draft Markdown & Add Metadata** |          I          |      **R**       |       A       |      I       |
| **4. Technical Accuracy Review**     |       **A/R**       |        C         |       I       |      I       |
| **5. Safety & Compliance Review**    |          C          |        I         |       I       |   **A/R**    |
| **6. Final Merge & Publish**         |          I          |      **R**       |     **A**     |      I       |

_(R = Responsible, A = Accountable, C = Consulted, I = Informed)_

---

### Lifecycle Trigger Points

Ownership responsibilities shift depending on where the asset is in its lifecycle:

1. **Design & Build Phase:** Project Managers are Accountable for ensuring the Documentation Team is resourced. SMEs are heavily Consulted.
2. **Commissioning Phase:** Technical Writers are Responsible for finalizing the baseline operations manuals. SMEs are Accountable for sign-off.
3. **Operations & Maintenance Phase:** The Operations Manager becomes the primary stakeholder, raising Jira tickets for the Documentation Team when SOPs require adjustment based on field conditions.

### Enforcement Mechanisms

- **Automated Audits:** The MkDocs build script scans all files for the `author` metadata field. If it is blank or contains a deprecated team name, the build fails and alerts the Documentation Architect.
- **SLA Tracking:** Jira dashboards track SME response times to review requests. Persistent bottlenecks are escalated to the Enterprise Documentation Control Board (EDCB).

---

_Document Owner: Principal Documentation Architect | Last Audit: Q2_
