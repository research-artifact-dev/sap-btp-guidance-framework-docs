# §1 Methodologies in the SAP BTP Guidance Framework

## §1.1 Purpose and Context

Within the SAP BTP Guidance Framework, methodologies occupy a distinct and deliberate position: they sit above technology choices. Before an architect selects a specific BTP service, a reference architecture, or a deployment model, there is a prior question that must be answered — *what strategy governs this domain?* The three methodologies in the framework exist to answer exactly that question, each for a different domain of concern. They provide structured, repeatable processes for analysing requirements, classifying use cases, and arriving at a principled strategy that can then be translated into concrete technology decisions.

The reason methodologies are treated as a separate layer — rather than embedded inside technology guides or reference architectures — is that they are intentionally technology-agnostic. An organisation running through the SAP Integration Solution Advisory Methodology will complete the majority of its work without naming a single BTP service. The output is a map of integration use cases, styles, and domains. Only once that map exists does it make sense to ask which BTP integration technology is the right fit. This sequencing prevents the common failure mode of tool-first thinking, where a team selects a product before fully understanding the problem space.

All three methodologies are positioned under the **Guidance for Architects** pillar of the SAP BTP Guidance Framework. They complement each other rather than compete: ISA-M addresses integration strategy, DAAM addresses data and analytics strategy, and AEM addresses application extension strategy. In practice, a large enterprise programme will engage with all three, since modern SAP landscapes involve integration, data flows, and extensions simultaneously. Understanding how they relate — and where their boundaries lie — is a key architectural concern in its own right.

## §1.2 Relationship to Other Framework Assets

The methodologies are the strategic entry point; they do not stand alone. Their outputs feed directly into the reference architectures, the technology mapping guides, and the domain-specific best practices that make up the rest of the SAP BTP Guidance Framework. An architect who completes an ISA-M engagement, for example, will produce an integration style classification and a domain assignment for each integration scenario. Those outputs are directly consumable by the integration reference architectures and the technology comparison guides published elsewhere in the framework.

The architecture diagram below illustrates how the three methodologies connect to the broader framework and to each other. It is the recommended starting point for communicating this layering to stakeholders who are new to the framework.

> 📐 **Architecture Diagram:** [`../diagrams/architecture.drawio`](../diagrams/architecture.drawio) — open in [draw.io](https://app.diagrams.net).

---

# §2 The Three Methodologies

## §2.1 Overview Table

| Methodology | Full Name | Domain | Key Output | Primary Related Framework Asset |
|---|---|---|---|---|
| **ISA-M** | SAP Integration Solution Advisory Methodology | Integration | Integration strategy map: styles, domains, and technology recommendations | Integration Reference Architectures, Integration Technology Comparison |
| **DAAM** | SAP Data and Analytics Advisory Methodology | Data & Analytics | Data and analytics strategy: architecture patterns, scenario classification, technology selection | Data & Analytics Reference Architectures, BTP Data Services Guide |
| **AEM** | SAP Application Extension Methodology | Application Extension | Extension strategy: extension type classification, side-by-side vs. in-app decisions, BTP capability mapping | Extension Architecture Guide, Extension Scenario Catalogue |

## §2.2 SAP Integration Solution Advisory Methodology (ISA-M)

ISA-M is the most widely adopted of the three methodologies and is typically the first one an organisation encounters when engaging with the SAP BTP Guidance Framework. Its core purpose is to give integration architects a structured way to define an integration strategy that is grounded in business use cases rather than product selection. The methodology proceeds through a layered analysis: it begins with **integration styles** (process integration, data integration, analytics integration, and user interface integration), then maps those styles to **integration domains** (cloud-to-cloud, cloud-to-on-premise, and so on), and finally arrives at **technology recommendations** that reflect the organisation's landscape and constraints.

A critical design principle of ISA-M is that it produces a *strategy*, not a project plan. The output is a living artefact — an integration solution map — that captures the organisation's classification of all known and anticipated integration scenarios. This map becomes the reference against which individual integration projects are evaluated. When a new integration requirement arises, the architect does not start from scratch; instead, they locate the new scenario on the existing map, identify the applicable style and domain, and apply the corresponding technology guidance.

ISA-M integrates directly with the integration-specific reference architectures in the framework. Once a scenario has been classified under ISA-M, the integration technology mapping layer translates that classification into a recommended BTP service set — for example, SAP Integration Suite for A2A and B2B process integration, or SAP Event Mesh for event-driven scenarios.

## §2.3 SAP Data and Analytics Advisory Methodology (DAAM)

DAAM provides a structured process for defining an organisation's data and analytics strategy on SAP BTP. The methodology is designed to address the growing complexity of modern data landscapes, where organisations must simultaneously manage historical reporting, real-time operational analytics, predictive models, and data sharing across business units and partners.

The methodology guides architects through a classification of analytics scenarios — from operational reporting and self-service BI through to enterprise-scale data warehousing and AI/ML workloads — and helps map those scenarios to the appropriate data architecture patterns available on SAP BTP. Critically, DAAM also considers data governance, data lifecycle management, and the relationship between transactional systems (such as SAP S/4HANA) and analytical platforms. This means its outputs are not purely technical; they include governance recommendations and organisational considerations that must be addressed alongside technology selection.

The primary related framework asset is the Data & Analytics Reference Architectures collection, which provides detailed architecture blueprints for each of the major scenario categories that DAAM produces. DAAM is also closely connected to SAP Datasphere and SAP Analytics Cloud documentation within the framework, since those services cover the majority of BTP data and analytics use cases.

## §2.4 SAP Application Extension Methodology (AEM)

AEM addresses a question that is central to any SAP customer operating in a cloud-first or RISE with SAP context: *when and how should SAP applications be extended, and through which mechanism?* The pressure to keep SAP core clean — avoiding modifications that complicate upgrades — while still meeting specific business requirements drives the need for a principled extension strategy. AEM provides exactly that.

The methodology classifies extension requirements into types: in-app extensions (within the SAP application's own extensibility framework), side-by-side extensions (built on SAP BTP and connected via APIs), and process extensions (automating or augmenting business processes without touching core logic). For each type, AEM provides decision guidance on the appropriate BTP capabilities, integration patterns, and lifecycle considerations. A key output is a documented extension strategy that records *why* a particular extension approach was chosen — a record that proves its value when new requirements arise or when the organisation considers upgrading its core SAP applications.

AEM has the tightest coupling to a specific framework asset of any of the three methodologies. The **Extension Architecture Guide** is effectively the reference companion to AEM: it documents the architectural patterns for each extension type in detail, with worked examples and technology mappings. Architects are expected to use AEM and the Extension Architecture Guide in tandem. See [docs/03-extension-architecture-guide.md](03-extension-architecture-guide.md) for the full guide.

---

# §3 How the Methodologies Relate to Each Other

The three methodologies are complementary by design, but they are not sequential in the way that phases of a project are sequential. An organisation does not complete ISA-M before starting DAAM; rather, it engages with whichever methodology is relevant to the programme of work at hand. In practice, the methodologies frequently overlap. An extension built using AEM will almost certainly require integration patterns identified by ISA-M, and may expose data that needs to be classified and governed under DAAM.

The most important relationship to understand is the one between AEM and ISA-M. When an extension scenario is identified through AEM and classified as a side-by-side extension, the connectivity between that extension and the core SAP application is itself an integration scenario that falls within ISA-M's scope. The AEM output does not replace ISA-M for that connectivity requirement; it provides the extension-side context that the integration architect needs when working through ISA-M. This hand-off point — where AEM scope ends and ISA-M scope begins — should be explicitly documented in the integration solution map produced by ISA-M.

Similarly, many data and analytics scenarios classified by DAAM originate as data extracts or event streams produced by extensions defined through AEM. Architects working on programmes where all three domains are active are strongly advised to establish a shared architecture backlog that spans all three methodologies, rather than running them as separate and independent workstreams.

---

# §4 Choosing the Right Methodology

## §4.1 Decision Guidance

| When to use | Methodology to start with |
|---|---|
| Primary driver is connecting systems, exchanging data between applications, or defining enterprise integration strategy | **ISA-M** |
| Primary driver is building a data platform, enabling analytics, or selecting BTP data services | **DAAM** |
| Primary driver is extending an existing SAP application without modifying the core | **AEM** |
| Programme involves integration, data, and extension concerns simultaneously | **All three** — run concurrently with a shared architecture forum |

## §4.2 Key Design Decision

| Decision | Choice Made | Why | Trade-off |
|---|---|---|---|
| Whether to run multiple methodologies concurrently or sequentially | Run all relevant methodologies concurrently, with a shared architecture forum to manage cross-methodology decisions | Programmes of meaningful scope span integration, data, and extension concerns. Sequential execution risks making decisions in one domain that are incompatible with requirements in another. Concurrency surfaces conflicts earlier. | Concurrent engagement increases up-front coordination overhead and requires architects with cross-domain fluency. For small, single-domain programmes, a single-methodology engagement is simpler and fully appropriate. |

---

# §5 Open Questions and Known Gaps

1. **DAAM coverage depth.** The current documentation of DAAM in the framework is less mature than ISA-M. In particular, guidance for AI/ML and real-time analytics workloads is not yet fully documented. Teams working on those scenarios should engage directly with SAP's Centre of Excellence for supplementary guidance.

2. **AEM versioning across SAP application releases.** AEM guidance was developed with a specific baseline of SAP S/4HANA extensibility capabilities in mind. As SAP S/4HANA Cloud and SAP BTP evolve, the methodology documentation should be reviewed and versioned to align with major SAP S/4HANA Cloud release cycles. This is not currently happening systematically.

3. **Cross-methodology dependency mapping.** There is no formal artefact in the framework that maps the outputs of one methodology to the inputs of another. The hand-off between AEM and ISA-M is understood informally but not documented as a standard deliverable. A cross-methodology interface document would reduce the risk of misalignment in large programmes.

4. **Tooling support for methodology execution.** All three methodologies are currently executed through workshop facilitation and document templates. There is no tooling (such as a structured questionnaire tool or a scenario catalogue application) that accelerates or standardises execution. The feasibility and priority of tooling support has not been formally assessed.

5. **Governance of methodology updates.** It is not currently documented who owns each methodology within SAP, how updates are proposed and approved, or what the communication channel is for practitioners who identify errors or gaps.
