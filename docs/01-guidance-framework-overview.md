# §1 SAP BTP Guidance Framework — Overview

## §1.1 Why This Framework Exists

SAP Business Technology Platform (SAP BTP) brings together application development, automation, integration, data and analytics, and artificial intelligence under a single extensible platform. That breadth is a strength — but it also means that architects, developers, and administrators face a wide range of decisions with far-reaching consequences. Without a structured compass, teams risk inconsistent patterns, duplicated effort, and solutions that are hard to operate or evolve.

The **SAP BTP Guidance Framework** was created to address exactly this. First presented at SBN IT Architect Day on April 9, 2024, by Katrin von Ahsen (Chief Product Expert, SAP BTP), the framework acts as a centralized, authoritative starting point for anyone adopting SAP BTP in an enterprise context. Rather than leaving each project team to discover best practices on their own, the framework curates proven decision guides, reference architectures, methodologies, and operational recommendations — organized around the audiences who need them most.

The framework is not a single document or a one-time deliverable. It is a living system of interlinked assets that covers the full lifecycle of a BTP solution: from initial architecture decisions, through hands-on development, to day-to-day administration and security hardening. This overview document introduces the framework's structure, its three audience pillars, the five solution domains it spans, and the types of content assets it provides. Subsequent documentation files in this set go deeper into each pillar and domain.

---

## §1.2 Scope and Intended Audience

This document — and the broader documentation set it belongs to — is intended for:

- **IT Architects** evaluating or designing solutions on SAP BTP
- **SAP Developers** building extensions, integrations, or new applications on the platform
- **BTP Administrators** responsible for security, operations, and platform configuration
- **Project leads and technical decision-makers** who need to understand where the authoritative guidance lives and how to navigate it

The goal is not to reproduce the full content of each asset (those are maintained in their own dedicated guides), but to give every reader a clear mental model of the framework as a whole.

---

# §2 Framework Structure

## §2.1 The Root Container and Its Layers

The SAP BTP Guidance Framework can be thought of as having three conceptual layers:

1. **Audience Pillars** — the primary organizational layer, separating guidance by role: Architects, Developers, and Administrators.
2. **Solution Domains** — a horizontal cross-cut across all pillars, representing the five capability areas of SAP BTP.
3. **Foundation Layer** — shared resources that underpin all pillars: Best Practices, Learning and Enablement, and Community.

The architecture diagram illustrates how these layers relate to one another and how specific assets sit within them. Open it now alongside this section — the colour coding maps directly to the component types described below.

> 📐 **Architecture Diagram:** [`../diagrams/architecture.drawio`](../diagrams/architecture.drawio) — open in [draw.io](https://app.diagrams.net).

This layered design reflects a deliberate choice: role-based organization makes it easier for each audience to find what is relevant to them, while the shared foundation layer prevents duplication of cross-cutting content such as security baselines or onboarding learning paths.

## §2.2 The Three Audience Pillars

Each pillar addresses a distinct role with distinct needs. The table below summarizes the pillars, their primary focus, and the key assets they contain.

| Pillar | Primary Focus | Key Assets |
|---|---|---|
| **Guidance for Architects** | Solution design, architecture patterns, methodology | Integration Architecture Guide, Extension Architecture Guide, SAP BTP Reference Architectures, SAP BTP Solution Diagram Design Repository, Business Process Blueprints, ISA-M / DAAM / AEM methodologies |
| **Guidance for Developers** | Building and delivering BTP solutions | SAP BTP Developer's Guide, Decision Guides, DevOps with SAP BTP |
| **Guidance for Administrators** | Platform operations and security | Security Recommendations, General Recommendations |

The Architects pillar is the most content-dense because architecture decisions have the widest blast radius — a wrong early choice about integration style or extension approach ripples through every subsequent build and operational task. The Developers pillar balances prescriptive guidance (the Developer's Guide, Decision Guides) with enablement for modern delivery practices (DevOps). The Administrators pillar is deliberately focused: it surfaces only what an operator needs to keep a BTP landscape secure, stable, and well-configured.

## §2.3 The Five Solution Domains

Cutting across all three audience pillars, SAP BTP organizes its technical capabilities into five solution domains. These domains are not isolated silos — a real enterprise solution almost always spans more than one — but they provide a useful vocabulary for scoping architecture discussions and selecting the right guidance assets.

| Domain | Description |
|---|---|
| **App Dev** | Building custom applications, extensions, and side-by-side scenarios on BTP |
| **Automation** | Workflow, robotic process automation (RPA), and intelligent process orchestration |
| **Integration** | Connecting SAP and non-SAP systems, APIs, events, and data flows |
| **Data and Analytics** | Data management, business intelligence, and advanced analytics capabilities |
| **Artificial Intelligence (AI)** | Embedding AI/ML capabilities into business processes and applications |

When navigating the framework, it is useful to first identify which solution domain (or domains) your project touches before selecting the relevant guidance assets. For example, an architect designing a side-by-side extension with AI-assisted features would draw primarily from the App Dev and AI domains within the Architects pillar.

## §2.4 Content Asset Types

The framework does not present all guidance in the same format. Different questions call for different types of assets:

- **Decision Guides** help teams make a well-reasoned choice between competing options (for example: which integration style to use, or which runtime to build on).
- **Reference Architectures** provide proven, repeatable solution patterns scoped to common enterprise scenarios.
- **Methodologies** offer structured approaches for larger architectural concerns — the three methodologies in the Architects pillar are ISA-M (Integration Solution Advisory Methodology), DAAM, and AEM.
- **DevOps Principles** guide delivery practices — pipelines, testing strategies, deployment automation — on SAP BTP.
- **Recommendations** are distilled best-practice statements for administrators covering security hardening and general platform configuration.

Understanding which asset type to reach for is as important as knowing which pillar to look in. A team that needs to *choose* between two integration approaches should start with a Decision Guide; a team that needs a *proven pattern* to start from should start with a Reference Architecture.

---

# §3 Guidance for Architects — Detail

The Architects pillar is the natural starting point for any new SAP BTP initiative. Its scope covers two major architectural concerns: **integration** (connecting the enterprise landscape) and **extension** (adding or adapting capability on top of SAP applications).

The **Integration Architecture Guide** and **Extension Architecture Guide** each address their domain end-to-end: principles, patterns, tool selection, and governance considerations. Alongside these, the **SAP BTP Reference Architectures** provide concrete, scenario-specific blueprints — ready-to-adapt starting points rather than abstract theory. The **SAP BTP Solution Diagram Design Repository** complements these by providing a consistent visual language for communicating architecture decisions across teams and stakeholders.

**Business Process Blueprints** bridge the gap between business capability design and technical architecture, making it possible to trace a business outcome back to the BTP components that deliver it.

The three methodologies deserve particular attention:

- **ISA-M (Integration Solution Advisory Methodology)** — a structured approach for defining and governing an enterprise integration architecture on SAP BTP.
- **DAAM (Data and Analytics Advisory Methodology)** — addresses data architecture and analytics strategy on SAP BTP.
- **AEM (Application Extension Methodology)** — guides teams in defining their extension strategy for SAP applications using BTP capabilities.

For a full treatment of the three methodologies, see [docs/04-methodologies.md](04-methodologies.md).

---

# §4 Guidance for Developers — Detail

The Developers pillar translates architecture decisions into implementation guidance. The **SAP BTP Developer's Guide** is the central reference — it covers development models, runtime choices, and hands-on patterns for building on BTP. It is designed to work alongside, not in isolation from, the Architects pillar: developers are expected to understand the architecture context their work sits within.

**Decision Guides** in the Developers pillar address the concrete choices that arise during implementation — for example, which programming model to adopt, how to handle authentication, or when to use an on-stack versus side-by-side extension approach. These are distinct from architectural Decision Guides in that they are scoped to implementation-level trade-offs rather than landscape-level ones.

**DevOps with SAP BTP** covers the delivery dimension: how to build CI/CD pipelines, automate testing, manage transport, and operate BTP solutions reliably. This reflects a deliberate design choice to treat DevOps not as an afterthought but as a first-class concern addressed within the framework itself.

---

# §5 Guidance for Administrators — Detail

The Administrators pillar is tightly scoped to the concerns of those who operate a BTP landscape day-to-day. It contains two primary asset groups:

- **Security Recommendations** — hardening guidelines, identity and access management configurations, and audit considerations specific to SAP BTP.
- **General Recommendations** — operational best practices covering account structure, resource management, monitoring, and platform configuration.

Both asset groups are structured as actionable recommendations rather than conceptual guidance, reflecting the operational nature of the administrator role.

---

# §6 Foundation Layer

Beneath all three pillars, the framework provides a shared foundation that benefits every audience:

- **Best Practices** — a curated set of cross-cutting principles that apply regardless of role or solution domain.
- **Learning and Enablement** — structured learning paths, tutorials, and hands-on resources for teams building BTP skills.
- **Community** — connection to the broader SAP BTP practitioner community, including forums, SAP Community content, and events such as SBN IT Architect Day.

The Foundation Layer ensures that the framework is not only a reference system but also an onramp — teams new to BTP can use it to get up to speed, while experienced teams can use it to stay current as the platform evolves.

---

# §7 Key Design Decisions

| Decision | Choice Made | Why | Trade-off |
|---|---|---|---|
| How to organize framework content | Primary organization by **audience role** (Architects / Developers / Administrators), with solution domains as a secondary cross-cutting dimension | Different roles have fundamentally different questions, timescales, and success criteria. Role-based organization minimizes cognitive load. | Content spanning multiple roles must be either duplicated or cross-referenced; the Foundation Layer mitigates this but some navigational overhead remains. |
| How to handle best practices and community | Placed in a shared Foundation Layer beneath all pillars, rather than within individual pillars | Prevents duplication and gives all roles equal access to cross-cutting guidance | The Foundation Layer may be less discoverable than pillar-specific content for first-time users |

---

# §8 Open Questions and Known Gaps

1. **Versioning and lifecycle of framework assets** — It is not yet documented how individual assets (e.g., a specific Reference Architecture) are versioned or retired as SAP BTP evolves. A lightweight versioning and deprecation policy would strengthen the framework's long-term usability.

2. **DAAM and AEM methodology details** — This overview introduces ISA-M, DAAM, and AEM by name. Dedicated deep-dive documentation for each is in [docs/04-methodologies.md](04-methodologies.md), but further coverage of DAAM in particular is acknowledged as incomplete.

3. **Cross-domain solution scenarios** — The five solution domains are described individually, but there is currently no documented guidance for the most common cross-domain combinations (e.g., Integration + AI, App Dev + Automation).

4. **Governance and update cadence** — It is unclear how frequently the framework is reviewed and updated, who owns updates to specific assets, and how the community can contribute corrections or new patterns.

5. **Relationship to SAP Discovery Center and SAP Help Portal** — The framework coexists with other SAP guidance surfaces. The boundaries and preferred navigation paths between these are not yet explicitly documented.
