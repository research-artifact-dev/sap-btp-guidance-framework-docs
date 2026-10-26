# §1 SAP BTP Reference Architectures

SAP BTP Reference Architectures are curated solution templates that provide architects with a structured starting point for designing solution architectures on the SAP Business Technology Platform. Rather than approaching each new integration or extension scenario from a blank slate, architects can draw on a library of validated, scenario-specific blueprints that encode the collective experience of SAP solution architects and the broader customer community. This significantly reduces the time required to move from a business requirement to a defensible technical design, while also promoting consistency across engagements.

Within the SAP BTP Guidance Framework, reference architectures sit under the **Guidance for Architects** pillar alongside Business Process Blueprints and the Integration Architecture Guide. They are one of four main content asset types — the others being Decision Guides, Methodologies, and DevOps guidance — and they represent the most concrete, scenario-grounded layer of architectural advice the framework provides. Where Decision Guides help teams choose between platform capabilities and Methodologies establish process discipline, reference architectures translate those choices into actionable, diagrammatic designs.

---

## §1.1 Hosting and Discovery

All SAP BTP Reference Architectures are hosted on the **SAP Discovery Center** ([discovery.sap.com](https://discovery.sap.com)). The Discovery Center acts as the single authoritative repository for browsing, filtering, and accessing reference architectures by use-case category, line of business, or relevant BTP service. Architects should treat the Discovery Center as the living source of truth; the content published there is maintained by SAP and updated as the platform evolves.

Because the Discovery Center is the canonical location, this documentation set does not attempt to replicate the full catalogue. Instead, the sections below describe the structural model that underpins every reference architecture, explain how to read and apply them, and capture the design decisions made in adopting this approach within the SAP BTP Guidance Framework.

---

## §1.2 Three-Part Structure of a Reference Architecture

Every SAP BTP Reference Architecture is composed of three elements that work together to give an architect both the visual and the narrative understanding needed to adapt the template to a specific customer context.

| Element | Description | Primary Audience |
|---|---|---|
| **Architecture Diagram** | A visual representation of the solution components, their relationships, and the data / integration flows between them. Produced according to the SAP BTP Solution Diagram Design Guideline (see §2). | All stakeholders — provides shared vocabulary |
| **Guiding Information** | Narrative content explaining the scenario context, design rationale, key assumptions, and recommended configuration choices. Accompanies the diagram to prevent misinterpretation. | Solution and enterprise architects |
| **Related Services and Missions** | A curated list of the BTP services involved in the architecture, linked to Discovery Center missions (hands-on guided trials) that allow teams to validate the design before committing to it. | Architects, developers, and project leads |

The three elements are deliberately interdependent. The diagram without the guiding narrative risks being applied out of context; the narrative without the diagram is harder to communicate to broader project teams; and both are incomplete without the pointer to services and missions that enable proof-of-concept validation.

---

# §2 SAP BTP Solution Diagram Design Guideline

As of **April 2024**, SAP introduced the **SAP BTP Solution Diagram Design Guideline** — a standardized visual language and set of conventions for creating solution diagrams across all BTP reference architectures. The guideline establishes consistent icon sets, grouping conventions, flow-line semantics, and colour coding so that any architect familiar with the standard can read a diagram produced by any other architect or SAP team without ambiguity.

The introduction of this guideline represents a meaningful maturation of the framework. Prior to its publication, diagram styles varied significantly between reference architectures and customer-authored designs, making it difficult to compare architectures or identify reuse opportunities at a glance. By adopting the guideline, teams contribute to a shared visual vocabulary that scales across organisations and reduces onboarding overhead for new architects joining an engagement.

The relationship between reference architecture components and the broader framework is illustrated in the architecture diagram below. Open it alongside this section — the swim-lane grouping maps directly to the layered structure described in the overview document.

> 📐 **Architecture Diagram:** [`../diagrams/architecture.drawio`](../diagrams/architecture.drawio) — open in [draw.io](https://app.diagrams.net).

---

## §2.1 Relationship to Other Framework Assets

Reference architectures do not stand alone. The table below shows how they connect to the other primary asset types within the SAP BTP Guidance Framework and clarifies where each asset type should be used in a typical architecture engagement.

| Framework Asset | Relationship to Reference Architectures | Typical Usage Phase |
|---|---|---|
| **Decision Guides** | Inform which services and integration patterns appear in a reference architecture; should be consulted before selecting a template | Pre-architecture / service selection |
| **Reference Architectures** | The scenario-specific design template; the primary artefact used during solution design | Solution design |
| **Business Process Blueprints** | Provide the business-process context that a reference architecture implements technically; drive scenario selection | Business requirements / scoping |
| **Integration Architecture Guide** | Provides cross-cutting integration patterns and governance rules that all reference architectures must respect | Design review / governance |
| **Methodologies** | Define the process and deliverable structure within which reference architectures are produced and reviewed | Engagement delivery |
| **DevOps Guidance** | Covers the operational lifecycle of solutions built using a reference architecture | Build, deploy, and operate |

---

# §3 How to Apply a Reference Architecture

When an architect identifies a candidate reference architecture on the Discovery Center, the recommended approach is to treat it as a **starting template**, not a finished design. The following steps describe a typical adaptation workflow:

1. **Validate scenario fit** — Confirm that the business process context described in the guiding information matches the customer's requirement. If it only partially matches, note the delta explicitly before proceeding.
2. **Review related Decision Guides** — Check whether any service-selection decisions in the template need to be revisited in light of the customer's specific constraints (data residency, licensing, existing landscape).
3. **Adapt the diagram** — Using the SAP BTP Solution Diagram Design Guideline, modify the reference architecture diagram to reflect the customer's actual landscape.
4. **Document deviations** — Any departure from the reference architecture should be recorded as an Architecture Decision Record (ADR) with a rationale. This protects the team during design reviews and audits.
5. **Leverage missions for validation** — Before finalising the design, use the linked Discovery Center missions to run a proof-of-concept on the BTP services involved. Missions reduce integration risk by surfacing configuration issues early.

---

# §4 Key Design Decisions

| Decision | Choice Made | Why | Trade-off |
|---|---|---|---|
| Reference architectures are documented by pointer to SAP Discovery Center rather than reproduced inline in this documentation set | Link to Discovery Center; do not copy diagram or guiding content locally | Discovery Center is the authoritative, actively maintained source. Reproducing content locally creates a maintenance burden and risks divergence from the latest SAP guidance. | Teams without reliable internet access during an engagement cannot reference the material offline. Mitigated by encouraging architects to download relevant artefacts at the start of an engagement. |
| Adopt the new Solution Diagram Design Guideline for all new diagram work | Standardised icon set and layout conventions from April 2024 | Establishes a shared visual vocabulary that scales across organisations and reduces onboarding overhead for new architects | Existing diagrams produced before April 2024 are not yet migrated to the new standard, creating inconsistency in the short term |

---

# §5 Open Questions / Known Gaps

| # | Open Question / Gap | Priority |
|---|---|---|
| OQ-01 | The April 2024 Solution Diagram Design Guideline has not yet been adopted uniformly across all existing Discovery Center reference architectures. Migration timeline is unknown. | Medium |
| OQ-02 | There is no documented process for customers or partners to submit new reference architecture candidates to SAP for inclusion in the Discovery Center. | Low |
| OQ-03 | The relationship between reference architectures and SAP Cloud ALM's artefact model has not been formally documented. It is unknown whether reference architecture diagrams can be imported into Cloud ALM. | High |
| OQ-04 | Offline / air-gapped usage of reference architectures (e.g., in regulated industries) is not addressed. | Medium |
| OQ-05 | Version history and deprecation policy for Discovery Center reference architectures — it is unclear how teams are notified when a reference architecture they have adopted is superseded or retired. | High |
