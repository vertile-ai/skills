## Why Coding Skills

Have you ever faced scenarios like these when working with AI-assisted code?

1. Spent too much time planning
2. Spent too much time requesting small modifications from various angles
3. Spent too much time understanding AI-generated code

If so, `skills` might help. It is a collection of opinionated but battle-tested instructions at the implementation-detail level for different coding languages, frameworks, and agent workflows. Sure, you can do spec-driven development — but what if you just want a quick start?

It covers the most common software requirements and provides a bottom-up strategy for AI to build modules. Whether it is a

- Video streaming platform
- 2D game
- 3D game
- Multi-tenant SaaS platform
- Instant messaging application
- ...

you name it! You should always be able to find a skill to start with. If not, we will strive to make it happen for you.

## 2 Major Principles

1. Every skill must be written and verified by a human. AI enhancement is acceptable, but no AI slop.
2. Every skill is battle-tested in a real-world environment.

## Why This Repo May Not Be for You

This repo is not the right fit if you want to pre-design the system architecture before writing any code.

## Repository Structure

- `app-coding-skills/` contains skills whose outcome is an application or application module, including web apps, mobile apps, desktop apps, games, and category-specific app workflows.
- Top-level skill folders are reserved for meta skills that improve agent behavior rather than generating a specific app category.
- `docs/` and `scripts/` contain validation policy and repo tooling.

## How It Works

Find the skill that suits your needs and install it using:

```bash
npx skills add https://github.com/vertile-ai/skills --skills <skill-folder>
```

For app coding skills, use the folder path, for example `app-coding-skills/live-chat`.
For meta skills, use the top-level folder, for example `gpt-5-5-prompt-optimize`.

You can find the full list in the [Full List](#full-list) section below.

## Full List

### Meta skills

| Skill | Description |
|-------|-------------|
| `gpt-5-5-prompt-optimize` | Optimize, rewrite, or diagnose GPT-5.5 prompts using OpenAI prompt-guidance patterns. |

### App coding skills

| Skill | Description |
|-------|-------------|
| `app-coding-skills-video-streaming` | Building a web-based video streaming platform. Covers ingest protocols, transcoding pipelines, adaptive delivery (HLS/DASH), real-time chat, CDN distribution, storage strategy, auth, and scalability. |
| `app-coding-skills-2d-game` | Developing a browser-based 2D game. Covers dependencies, code patterns, module design, WASM/Worker/WebGL trade-offs, and browser APIs for all six web 2D game drives: control, system, rule, content, physics, and network. |
| `app-coding-skills-3d-game` | Developing a browser-based 3D game. Covers renderer selection, scene graph design, asset pipeline, memory management, shader strategy, physics integration, and browser API trade-offs across six 3D game drives: render, control, system, content, physics, and network. |

### Taxonomy philosophy (dual-axis)

The taxonomy now uses two complementary axes:

1. **Business axis**: narrow product-type categories with distinct implementation pressures (niche-by-category-size, not popularity).
2. **Architecture axis**: reusable application-layer module categories admitted only when they benefit at least 10 business categories and keep explicit overlap boundaries.

Broad buckets like plain `SaaS` are intentionally excluded.

Manifest and policy docs:

- `docs/taxonomy-manifest.yaml`
- `docs/skill-authoring-policy.md`

Architecture-category evidence contract:

- Canonical beneficiary/overlap/source-audit evidence lives in `app-coding-skills/<category>/references/implementation.md`.
- Manifest rows store machine-readable proof pointers and thresholds only.

### Operations & Admin Workflows

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-ops-control-center` | Operational command center for multi-tenant B2B systems: incidents, alerts, SLA breaches, and escalation state. | Tier 3 |
| `app-coding-skills-facility-ops` | Facility operations system for site access, maintenance requests, occupancy events, and contractor workflows. | Tier 2 |
| `app-coding-skills-incident-console` | Incident response workspace focused on alert triage, severity routing, on-call ownership, and timeline evidence. | Tier 1 |
| `app-coding-skills-property-portal` | Property operations portal for lease lifecycle, work orders, notices, and tenant communication artifacts. | Tier 1 |
| `app-coding-skills-tenant-portal` | Tenant self-service portal for requests, documents, payments, and operational status tracking. | Tier 1 |
| `app-coding-skills-procurement-portal` | Procurement operations workspace for requisitions, approvals, vendor interactions, and PO state transitions. | Tier 1 |

### Field, Dispatch & Scheduling

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-field-service` | Field service platform for technician assignment, visit execution, checklists, and completion evidence. | Tier 3 |
| `app-coding-skills-dispatch-board` | Real-time dispatch board for allocating jobs to agents/vehicles with live state and exception handling. | Tier 2 |
| `app-coding-skills-route-planner` | Route planning software for optimizing stop sequences and travel windows under operational constraints. | Tier 1 |
| `app-coding-skills-booking-engine` | Booking engine for reservable resources with slot generation, conflict prevention, and hold/confirm flows. | Tier 1 |
| `app-coding-skills-appointment-scheduler` | Appointment scheduler for time-bound services with availability, buffers, no-show handling, and rebooking. | Tier 1 |
| `app-coding-skills-queue-management` | Queue management software for tokenized service order, wait-time estimation, and lane prioritization. | Tier 1 |

### Commerce & Finance Operations

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-invoice-ops` | Invoice operations software for draft/finalize/void cycles, tax handling, and reconciliation workflows. | Tier 3 |
| `app-coding-skills-subscription-billing` | Subscription billing product for recurring plans, upgrades/downgrades, proration, and dunning. | Tier 2 |
| `app-coding-skills-expense-management` | Expense management workflow for submission, policy checks, approvals, reimbursement, and audit evidence. | Tier 1 |
| `app-coding-skills-ecommerce-admin` | E-commerce admin console for catalog, order, fulfillment, discount, and refund operations. | Tier 1 |
| `app-coding-skills-marketplace-seller` | Marketplace seller workspace for listing, inventory, order handling, payout visibility, and disputes. | Tier 1 |
| `app-coding-skills-returns-portal` | Returns portal for RMA creation, eligibility rules, reverse-logistics state, and refund closure. | Tier 1 |

### Support & Collaboration

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-customer-support` | Customer support desk for ticket intake, assignment, SLA control, and resolution playbooks. | Tier 3 |
| `app-coding-skills-live-chat` | Live chat messaging system with tenant/user rooms, agent assignment, and transcript persistence. | Tier 2 |
| `app-coding-skills-knowledge-base` | Knowledge base platform for authored docs, revisions, publication workflow, and discoverable search. | Tier 1 |
| `app-coding-skills-community-forum` | Community forum software for threaded discussions, moderation, reputation, and abuse controls. | Tier 1 |
| `app-coding-skills-crm-workspace` | CRM workspace for contact/account timelines, activity capture, and pipeline handoff workflows. | Tier 1 |
| `app-coding-skills-document-signing` | Document signing workflow with template generation, signer state tracking, and tamper-evident audit logs. | Tier 1 |

### People, Learning & Engagement

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-job-board` | Job board product for role publishing, candidate discovery, and application intake at scale. | Tier 3 |
| `app-coding-skills-applicant-tracking` | Applicant tracking system with stage transitions, interviewer coordination, and hiring decision logs. | Tier 2 |
| `app-coding-skills-learning-platform` | Learning platform for curriculum delivery, enrollment progression, assessment, and completion analytics. | Tier 1 |
| `app-coding-skills-exam-proctoring` | Exam proctoring system for exam session control, identity checkpoints, violation events, and audit review. | Tier 1 |
| `app-coding-skills-event-ticketing` | Event ticketing software for inventory allocation, checkout windows, issuance, and gate validation. | Tier 1 |
| `app-coding-skills-donation-platform` | Donation platform for campaign funding, recurring pledges, receipts, and impact reporting workflows. | Tier 1 |

### Vertical Operations

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-telehealth-portal` | Telehealth portal for appointment intake, virtual visit orchestration, and clinician/patient workflow sync. | Tier 3 |
| `app-coding-skills-patient-intake` | Patient intake workflow for demographics, consent, insurance details, and pre-visit data quality checks. | Tier 2 |
| `app-coding-skills-restaurant-ordering` | Restaurant ordering platform for menu/cart/checkout, order lifecycle, and fulfillment channel routing. | Tier 1 |
| `app-coding-skills-kitchen-display` | Kitchen display system for ticket sequencing, prep station routing, and expo/ready state transitions. | Tier 1 |
| `app-coding-skills-inventory-control` | Inventory control software for stock ledger movements, cycle counts, and reorder policy workflows. | Tier 1 |
| `app-coding-skills-warehouse-console` | Warehouse console for receiving, put-away, pick-pack-ship, and exception processing. | Tier 1 |

### Architecture — Identity & Access Modules

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-auth-social-sso` | Auth module for Google/GitHub social sign-in, account linking boundaries, and session lifecycle hardening. | Tier 2 |
| `app-coding-skills-tenant-rbac-policy` | Tenant-scoped RBAC policy module for role/permission evaluation, policy versions, and audit-safe authorization evolution. | Tier 1 |

### Architecture — Workflow & Integration Modules

| Skill | Description | Tier |
|---|---|---|
| `app-coding-skills-async-job-orchestration` | Background job orchestration module with idempotency, retry/backoff, dead-letter handling, and compensation-safe workflow defaults. | Tier 2 |
| `app-coding-skills-domain-event-pubsub` | Domain-event pub/sub module with contract versioning, outbox publishing, and idempotent consumer boundaries. | Tier 1 |
| `app-coding-skills-object-storage-pipeline` | Object-storage upload/retrieval module with signed URL lifecycle, metadata consistency, and secure ingest boundaries. | Tier 1 |

### Architecture tier notes

- Tier 1: `SKILL.md` + `references/implementation.md` under `app-coding-skills/<category>/` with required beneficiary/overlap evidence sections.
- Tier 2: Tier 1 + at least 3 source-audit rows + explicit README coverage.
- Tier 3: Tier 2 + smoke validation evidence.
