# Enterprise Taxonomy Design

## 1. Taxonomy Overview

The Enterprise Taxonomy Design establishes the controlled vocabulary and hierarchical classification system used across the Enterprise Infrastructure Knowledge Base.

In a multidisciplinary infrastructure organization, ambiguous terminology creates operational risk. (For example, a "Node" in smart city IT infrastructure means something entirely different than a "Node" in structural engineering). This taxonomy enforces a standardized, unambiguous lexicon aligned with ISO 19650 and civil engineering best practices, ensuring that search queries return precise, context-aware results.

---

### Objectives

- **Standardize Vocabulary:** Eliminate synonyms and acronym confusion across different engineering disciplines (e.g., Rail vs. Civil vs. Utilities).
- **Enhance Search Relevancy:** Provide a structured metadata framework that powers faceted search within the MkDocs environment.
- **Enable Content Interoperability:** Ensure documentation taxonomy aligns with the tagging structures used in our Enterprise Asset Management (EAM) software and Jira Service Desk.
- **Support Asset Lifecycles:** Classify information according to where an asset sits in its physical lifecycle (Design, Build, Maintain, Decommission).

---

### Core Taxonomic Facets

Our taxonomy uses a faceted classification approach. Every piece of documentation is categorized across four distinct dimensions (facets).

#### Facet 1: Domain (The "Where")

Identifies the primary engineering or operational division.

- `domain:smart-city`
- `domain:rail-transit`
- `domain:civil-highways`
- `domain:water-utilities`
- `domain:energy-grid`

#### Facet 2: Asset Class (The "What")

Identifies the physical or digital asset being documented. We align broadly with Uniclass 2015 asset classifications.

- `asset:bridge-suspension`
- `asset:rail-signaling-system`
- `asset:iot-traffic-sensor`
- `asset:pump-station-hydraulic`
- `asset:power-substation`

#### Facet 3: Information Type (The "Format")

Identifies the structural purpose of the document (aligning with our Information Architecture Topic Types).

- `type:sop` (Standard Operating Procedure)
- `type:reference` (Engineering tables, specifications)
- `type:concept` (System overviews, architecture)
- `type:troubleshooting` (Fault resolution)
- `type:policy` (Regulatory, health and safety)

#### Facet 4: Lifecycle Phase (The "When")

Identifies the temporal state of the asset or project.

- `phase:01-design`
- `phase:02-construction`
- `phase:03-commissioning`
- `phase:04-operations`
- `phase:05-maintenance`
- `phase:06-decommissioning`

---

### Controlled Vocabulary & Synonym Management

To prevent search fragmentation, the Enterprise Documentation Control Board (EDCB) maintains a strict "Use / Do Not Use" registry.

| Approved Term (Use)                    | Rejected Synonym (Do Not Use)    | Context / Definition                                     |
| :------------------------------------- | :------------------------------- | :------------------------------------------------------- |
| **Uninterruptible Power Supply (UPS)** | Battery Backup, Power Pack       | Use only for industrial-grade grid backup systems.       |
| **Standard Operating Procedure (SOP)** | Work Instruction, Guide, How-To  | Formal, step-by-step operational tasks.                  |
| **Preventive Maintenance (PM)**        | Routine Check, Scheduled Service | Time-based or meter-based maintenance cycles.            |
| **Incident**                           | Crash, Event, Problem            | Any unplanned interruption to an infrastructure service. |

---

### Governance & Tagging Mechanisms

1. **Frontmatter Enforcement:** The MkDocs build pipeline includes a continuous integration (CI) script that validates Markdown frontmatter. If a document uses an unapproved tag in its YAML header, the build fails and alerts the author.
2. **Taxonomy Updates:** The taxonomy is not static. If a new smart city technology is procured, the Lead Systems Engineer must submit a Jira ticket to the Documentation Architect to formalize the new nomenclature before documentation begins.
3. **Faceted Search:** By structuring our tags as `category:value` (e.g., `phase:05-maintenance`), we enable field technicians to filter the search bar specifically for maintenance documents, filtering out irrelevant design specs.

### Best Practices for Content Authors

- **Tag for the User, Not the Author:** Consider what terms a field technician is likely to type into a search bar at 2:00 AM during a storm.
- **Avoid Over-Tagging:** Limit documents to a maximum of 5-7 highly relevant tags. Over-tagging dilutes search relevancy.
- **Consult the Registry:** Always check the EDCB Controlled Vocabulary list in Confluence before inventing a new acronym.

---

_Document Owner: Principal Information Architect | Last Audit: Q1_
