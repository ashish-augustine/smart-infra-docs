# Documentation Lifecycle Model

## 1. Lifecycle Overview

The Enterprise Documentation Lifecycle Model defines the standard progression of all technical content from initial conception to final deprecation.

Because our documentation directly governs the safe operation of physical infrastructure, it cannot exist in a static state. This lifecycle ensures that documentation evolves in lockstep with the physical assets it describes, maintaining strict alignment with ISO 19650 information delivery cycles.

---

### Objectives

- **Maintain Accuracy:** Ensure content is continuously validated against the current operational state of the infrastructure.
- **Prevent Clutter:** Establish strict archiving protocols so outdated procedures do not confuse field technicians.
- **Align with Engineering Phases:** Map documentation deliverables to specific milestones in civil and systems engineering projects.

---

### The 5-Phase Documentation Lifecycle

The following diagram illustrates the standard lifecycle for Tier 1 and Tier 2 documentation within our Docs-as-Code ecosystem.

```mermaid
stateDiagram-v2
    [*] --> Phase1_Creation: Project Kickoff / ECR

    state Phase1_Creation {
        Drafting --> PeerReview
    }

    Phase1_Creation --> Phase2_Validation: Pull Request Opened

    state Phase2_Validation {
        SME_Review --> HSEQ_Audit
        HSEQ_Audit --> SME_Review: Revisions Required
    }

    Phase2_Validation --> Phase3_Publication: PR Approved & Merged

    state Phase3_Publication {
        CI_CD_Build --> Live_KnowledgeBase
    }

    Phase3_Publication --> Phase4_Maintenance: Asset Operational

    state Phase4_Maintenance {
        Scheduled_Audit --> Minor_Updates
        Minor_Updates --> Scheduled_Audit
    }

    Phase4_Maintenance --> Phase1_Creation: Major System Upgrade
    Phase4_Maintenance --> Phase5_Deprecation: Asset Decommissioned

    state Phase5_Deprecation {
        Archived_in_Git --> Removed_from_Index
    }

    Phase5_Deprecation --> [*]
```
