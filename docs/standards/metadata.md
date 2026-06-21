# Enterprise Metadata Standards

## 1. Standards Overview

The Enterprise Metadata Standards dictate how we tag, track, and classify information within the MkDocs environment.

While the Enterprise Taxonomy provides the vocabulary, metadata is the machine-readable application of that vocabulary. Every Markdown document in this repository must contain a valid YAML frontmatter block. This metadata is the foundation of our automated governance pipeline—it powers faceted search, drives automated content audit alerts, and ensures ISO 19650 compliance tracking.

---

### Objectives

- **Enable Advanced Search:** Allow users to filter results by asset class, domain, or document tier.
- **Automate Lifecycle Management:** Use the `date_next_review` field to trigger automated Jira tickets when a document is nearing expiration.
- **Ensure Traceability:** Maintain a strict ledger of document ownership and review status.

---

### Required YAML Frontmatter Schema

The following schema must be placed at the very top of every `.md` file. The CI/CD pipeline will reject any pull request where a mandatory metadata field is missing or malformed.

```yaml
---
title: "Document Title"
document_id: "Unique Alphanumeric ID"
description: "A 1-2 sentence summary of the document's purpose."
author: "Owning Team or Individual"
date_created: YYYY-MM-DD
date_updated: YYYY-MM-DD
date_next_review: YYYY-MM-DD
document_tier: [1, 2, or 3]
domain: "Taxonomy Facet 1"
asset_class: "Taxonomy Facet 2"
tags: [array, of, lowercase, taxonomy, tags]
review_status: "Draft | Under Review | Approved | Deprecated"
---
```
