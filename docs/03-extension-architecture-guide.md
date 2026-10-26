# Extension Architecture Guide

> Part of the SAP BTP Guidance Framework — Guidance for Architects

---

## §1 Purpose and Context

When organisations extend SAP solutions — whether S/4HANA, SAP SuccessFactors, or any other core product — the single most consequential early decision is choosing the right technical building block. Choose too loosely coupled and you sacrifice access to native platform capabilities; choose too tightly coupled and you accumulate upgrade risk and maintenance burden. The Extension Architecture Guide exists precisely to navigate this tension in a structured, repeatable way.

The guide is a decision artefact within the SAP BTP Guidance Framework, published under the "Guidance for Architects" pillar and made available on the SAP Discovery Center (added April 2024). Its primary purpose is to give architecture teams a common vocabulary and a phased methodology for mapping a business extension requirement all the way through to a specific set of technical building blocks. Rather than presenting an exhaustive catalogue of technologies and leaving the selection to intuition, the guide encodes accumulated SAP field experience into explicit decision paths.

Critically, the guide is not a one-shot checklist. It is designed to be run iteratively: as a team's understanding of the extension use case deepens — through spikes, prototypes, or stakeholder feedback — they re-enter the three phases with updated inputs. This iterative posture is intentional. Extension decisions made at the beginning of a project are rarely complete, and the guide accommodates revision without requiring teams to start from scratch.

---

## §2 The Three-Phase Methodology

The guide structures extension decision-making into three sequential but revisitable phases. Each phase has clearly defined inputs and outputs, ensuring that decisions are grounded in prior analysis rather than technology preference.

### §2.1 Phase Overview

| Phase | Name | Key Input | Key Output |
|-------|------|-----------|------------|
| **Phase 1** | Assess Extension Use Case | System context, business requirements | Identified extension use case |
| **Phase 2** | Assess Extension Technology | Extension use case, extension styles | Extension technology mapping |
| **Phase 3** | Define Extension Target Solution | Technology mapping, decision guidance assets | Colour-coded target solution table |

### §2.2 Phase 1 — Assess Extension Use Case

Phase 1 establishes the business and technical context before any technology conversation begins. The team starts with the **system context**: which SAP product is being extended, what its current deployment model is, and what organisational constraints apply (e.g., clean-core policies, upgrade cadence commitments). From that foundation, they articulate the **business and context requirements** — the functional gap or process improvement that the extension must address.

The output of Phase 1 is a clearly scoped **application extension use case**: a statement of what needs to be extended, why, and what user or integration scenario it serves. This use case becomes the stable anchor for the subsequent phases. Teams that skip or rush Phase 1 frequently find themselves revisiting technology choices because the underlying use case was ambiguous.

### §2.3 Phase 2 — Assess Extension Technology

Phase 2 is the analytical core of the guide. It takes the extension use case from Phase 1 and routes it through two layers of classification: **extension style** and **extension task**. Extension styles are high-level patterns (for example, P02 — New User Interface) that describe the nature of the change. Within each style, one or more **extension tasks** decompose the work into discrete technical concerns.

The **Extension Technology Mapping Diagram** then maps each extension task to the set of viable **technical extension building blocks**. This diagram is the intellectual centrepiece of the guide. For the full visual representation of how content assets (including the Extension Architecture Guide) connect within the framework, see:

> 📐 **Architecture Diagram:** [`../diagrams/architecture.drawio`](../diagrams/architecture.drawio) — open in [draw.io](https://app.diagrams.net).

Building blocks are organised into two **extension domains**:

- **Core Solution Extension Domain** — building blocks that operate within or directly adjacent to the core SAP system (e.g., ABAP-based extensibility, Dynpro, WebDynpro ABAP).
- **Side-by-Side Extension Domain** — building blocks deployed on SAP BTP, decoupled from the core (e.g., SAP Build Apps, SAP Mobile Services, SAPUI5 on BTP).

An important nuance is that a single extension task can be legitimately addressed by building blocks from *both* domains. The guide does not force a binary choice; it surfaces the full option set and defers the final selection to Phase 3, where team-specific constraints are applied.

### §2.4 Phase 3 — Define Extension Target Solution

Phase 3 synthesises the technology mapping into an actionable target. The team applies **decision guidance assets** — constraint rules, fit criteria, and reference patterns — to the candidate building blocks identified in Phase 2, and produces an **extension target solution**: a colour-coded technology mapping table that records, for each extension task, which building block has been selected and at what confidence level.

The colour coding (typically green / amber / red) is a deliberate communication device. It makes architectural decisions legible to stakeholders who are not deep SAP technologists, and it flags areas of uncertainty that warrant further investigation before commitment.

---

## §3 Extension Style P02 — New User Interface: Worked Example

To make the methodology concrete, consider **Extension Style P02 — New User Interface**. This style covers scenarios where a team needs to deliver a net-new user interface on top of an existing SAP solution, rather than modifying a standard screen.

The primary extension task within P02 is **Create custom UI**. The Extension Technology Mapping for this task surfaces the following candidate building blocks:

| Building Block | Extension Domain | Typical Fit |
|----------------|-----------------|-------------|
| Classic Extensibility: Dynpro | Core Solution | Legacy ABAP applications requiring tight transactional integration |
| Classic Extensibility: WebDynpro ABAP | Core Solution | Web-based ABAP UI with moderate coupling to backend |
| SAPUI5 | Side-by-Side | Modern, responsive web UIs; high design flexibility |
| SAP Fiori Elements | Side-by-Side | Rapid UI generation from OData annotations; lower custom code |
| SAP Mobile Services | Side-by-Side | Native or hybrid mobile applications |
| SAP Build Apps | Side-by-Side | Low-code / no-code UI for citizen developers or rapid prototyping |

The table illustrates a recurring pattern in the guide: core solution domain options (Dynpro, WebDynpro ABAP) carry stronger coupling to the ABAP stack and are generally suitable only when the team has committed to a long-term ABAP investment or when the use case demands deep transactional integration. The side-by-side options offer greater flexibility and better alignment with clean-core principles but introduce an additional runtime to operate and secure on BTP.

In practice, a Phase 3 assessment for a P02 use case on S/4HANA Cloud Public Edition would typically rule out Dynpro and WebDynpro ABAP on policy grounds (the clean-core constraint), leaving SAPUI5, SAP Fiori Elements, SAP Build Apps, and SAP Mobile Services as the active candidates. The final selection then turns on factors such as developer skill availability, design complexity, and whether the UI needs to run offline on mobile devices.

---

## §4 Key Design Decisions

| Decision | Choice Made | Why | Trade-off |
|---|---|---|---|
| Organise building blocks by extension domain (core vs. side-by-side) rather than by technology generation or maturity | Two-domain model: Core Solution Extension Domain and Side-by-Side Extension Domain | Domain classification directly reflects the clean-core / upgrade-impact trade-off that most architecture teams must make explicit. Grouping by domain makes that trade-off visible in the mapping output. | The two-domain model can over-simplify. Some building blocks (e.g., SAPUI5 deployed within the ABAP stack) span both domains depending on deployment choice. Teams must apply additional judgement at the domain boundary. |
| Use a colour-coded target solution table as the Phase 3 output | Green / amber / red colour coding per building block | Makes architectural decisions legible to non-technical stakeholders and flags uncertainty areas explicitly | Colour coding is subjective; different team members may rate the same building block differently. A shared rubric for assigning colours should be agreed before Phase 3. |

---

## §5 Integration with the Broader SAP BTP Guidance Framework

The Extension Architecture Guide does not operate in isolation. It sits within a layered set of guidance assets within the SAP BTP Guidance Framework.

Upstream, the guide consumes outputs from landscape and integration architecture work: the system context required in Phase 1 is typically sourced from an integration landscape diagram or an enterprise architecture model. Downstream, the colour-coded target solution table produced in Phase 3 feeds directly into solution design artefacts — sprint planning, build vs. buy assessments, and infrastructure sizing discussions.

The guide is also designed to be used alongside the **SAP BTP Solution Diagrams and Icons** toolkit and the **SAP Integration Solution Advisory Methodology (ISA-M)**. Where ISA-M addresses integration style selection (messaging, API, event-driven), the Extension Architecture Guide addresses extension style selection. The two are complementary and should be run in parallel when a project involves both integration and extension concerns — as is common in greenfield S/4HANA implementations.

For a full treatment of ISA-M and the other methodologies, see [docs/04-methodologies.md](04-methodologies.md).

---

## §6 Open Questions / Known Gaps

1. **Domain boundary for hybrid deployments.** The two-domain model does not yet provide explicit guidance for building blocks deployed in hybrid or embedded topologies (e.g., SAPUI5 on the ABAP Frontend Server vs. BTP). A decision tree or qualifying criteria is needed.

2. **Coverage of extension styles beyond P02.** This document uses P02 (New User Interface) as the sole worked example. The full guide covers additional styles (process extension, data extension, integration extension, etc.). Equivalent worked examples for at least two further styles should be added.

3. **Versioning of the Extension Technology Mapping Diagram.** The diagram needs a version stamp and a change log, and should be reconciled with the April 2024 SAP Discovery Center release.

4. **Guidance for regulated industries.** Teams in financial services, healthcare, or defence may face additional constraints (data residency, certification requirements) that affect building block eligibility. These are not currently surfaced as first-class inputs in Phase 1.

5. **Phase 3 output template.** The colour-coded target solution table is described but no standard template file has been linked. A template should be referenced or embedded here.

6. **Relationship to SAP Activate methodology.** It is not yet documented at which Activate phase (Prepare, Explore, Realize) each phase of the guide is expected to be executed.
