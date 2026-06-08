# 🏢 Enterprise Microsoft Operations Ontology

> A comprehensive OWL/RDF ontology describing the full operational model of a large enterprise built on the Microsoft technology stack.

![Ontology Graph](enterprise-microsoft-operations-ontology-graph.png)

---

## 📖 Overview

This ontology formally describes how a large enterprise organization operates using Microsoft tools — from identity and collaboration through to cloud infrastructure, business applications, security operations, and beyond.

The model covers **30+ entity classes**, **100+ properties**, and **40+ named relationships** spanning the full Microsoft ecosystem: Microsoft 365, Azure, Dynamics 365, Power Platform, Microsoft Sentinel, and more.

---

## 📁 Repository Contents

| File | Description |
|------|-------------|
| `enterprise_microsoft_ontology.rdf` | The OWL/XML ontology file — the primary artifact |
| `enterprise-microsoft-operations-ontology-graph.png` | Visual graph rendering of all entities and relationships |
| `README.md` | This file |

---

## 🗂️ Ontology Scope

The ontology is organized into **10 functional domains**:

### 1. 🏛️ Organizational Structure
`Company` · `BusinessUnit` · `Department` · `CostCenter` · `Office`

Models the legal entity, divisional hierarchy, departmental breakdown, and financial cost center mapping as used in **Dynamics 365 Finance** and **Entra ID**.

### 2. 👤 People & Identity
`Employee` · `Contractor` · `Role` · `Team`

Each employee is linked to their **Entra ID** account, **Outlook** mailbox, **OneDrive**, software licenses, hardware assets, and HR record. Manager hierarchy is captured via the `reportsTo` relationship and team membership.

### 3. 📋 Projects & Agile Delivery
`Project` · `Sprint` · `WorkItem` · `Milestone`

Full project lifecycle tracked in **Azure DevOps** and **Dynamics 365 Project Operations**. Supports Agile methodologies (Scrum, SAFe, Kanban, Waterfall) with work item types: Epic, Feature, User Story, Bug, Task, and Test Case.

### 4. ☁️ Azure Cloud Infrastructure
`AzureSubscription` · `AzureResourceGroup` · `AzureResource` · `AzurePolicy`

Resource hierarchy from subscription → resource group → individual resource. Captures SKU, region, monthly cost (**Azure Cost Management**), provisioning state, and governance via **Azure Policy**.

### 5. 🌐 Microsoft 365 Collaboration
`M365Tenant` · `TeamsChannel` · `SharePointSite` · `OneDriveDrive` · `OutlookMailbox` · `CalendarEvent`

The full M365 collaboration surface — tenant root, Teams groups and channels, SharePoint sites, mailboxes, and calendar events.

### 6. ⚡ Power Platform
`PowerApp` · `PowerAutomateFlow` · `PowerBIReport` · `PowerBIDataset` · `DataverseTable`

End-to-end Power Platform chain including data lineage: Dataverse tables → Power BI datasets → reports, and flow triggers from Power Apps.

### 7. 💼 Dynamics 365 Business Applications
`CRMAccount` · `CRMContact` · `SalesOpportunity` · `SalesQuote` · `SalesOrder` · `ServiceCase` · `FinanceJournal` · `PurchaseOrder` · `Vendor` · `Invoice`

Full **lead-to-cash** and **procure-to-pay** chains across Dynamics 365 Sales, Customer Service, and Finance.

### 8. 💻 Asset & License Management
`HardwareAsset` · `SoftwareLicense` · `IntuneDevice` · `CompliancePolicy`

Hardware inventory, Microsoft software licensing (EA, CSP, MCA, MPSA), Intune device enrollment, and compliance policy assignment.

### 9. 🔒 Security & Governance
`SecurityIncident` · `DefenderAlert` · `DataClassification` · `AuditLog` · `ConditionalAccessPolicy`

Security operations coverage across **Microsoft Sentinel**, **Defender XDR**, **Microsoft Purview** (sensitivity labels, audit logs), and **Entra ID Conditional Access**.

### 10. 🎓 HR & Learning
`HRRecord` · `TrainingCourse` · `PerformanceReview`

Employee lifecycle in **Dynamics 365 Human Resources** and learning management via **Microsoft Viva Learning** and **Viva Goals**.

---

## 🔗 Key Relationships

| From | Relationship | To |
|------|-------------|-----|
| `Company` | hasBusinessUnit | `BusinessUnit` |
| `Employee` | reportsTo | `Employee` |
| `Employee` | hasEntraIdUser | `EntraIDUser` |
| `Employee` | assignedLicense | `SoftwareLicense` |
| `Project` | hasSprint | `Sprint` |
| `Sprint` | containsWorkItem | `WorkItem` |
| `AzureSubscription` | containsResourceGroup | `AzureResourceGroup` |
| `SalesOpportunity` | hasQuote → convertedToOrder → generatesInvoice | `Invoice` |
| `PowerBIDataset` | sourcedFromDataverse | `DataverseTable` |
| `SecurityIncident` | triggeredByAlert | `DefenderAlert` |
| `HardwareAsset` | enrolledAsIntuneDevice | `IntuneDevice` |

---

## 🛠️ Tools & Resources

### Microsoft Ontology Playground
**[@microsoft/Ontology-Playground](https://github.com/microsoft/Ontology-Playground)** | [https://microsoft.github.io/Ontology-Playground/](https://microsoft.github.io/Ontology-Playground/)

A free, open-source web application for learning about ontologies and Microsoft Fabric IQ. Explore pre-built ontologies, design your own in a visual editor, export as RDF/XML, and share interactive diagrams — all from a fully static site with zero backend dependencies.

---

## 🧩 Namespace

| Prefix | URI |
|--------|-----|
| `ont:` | `http://example.org/ontology/enterprise-msft/` |
| `owl:` | `http://www.w3.org/2002/07/owl#` |
| `rdf:` | `http://www.w3.org/1999/02/22-rdf-syntax-ns#` |
| `rdfs:` | `http://www.w3.org/2000/01/rdf-schema#` |
| `xsd:` | `http://www.w3.org/2001/XMLSchema#` |

---

## 🔧 Extending the Ontology

To adapt this ontology to your organization:

1. Replace `http://example.org/ontology/enterprise-msft/` with your own base URI (e.g., `https://ontology.contoso.com/enterprise/`)
2. Update `company_tenantId` and `company_domainName` with your actual Microsoft tenant values
3. Add subclasses using `<rdfs:subClassOf>` to model specialized entity types
4. Add instance data (individuals) to represent real objects in your organization

---

## 📄 License

This ontology is released under the [MIT License](LICENSE). You are free to use, adapt, and redistribute it with attribution.

---

## 🙏 Acknowledgements

Built using open standards:
- [OWL 2 Web Ontology Language](https://www.w3.org/TR/owl2-overview/)
- [RDF 1.1 Concepts](https://www.w3.org/TR/rdf11-concepts/)
- [XML Schema Datatypes](https://www.w3.org/TR/xmlschema-2/)

Microsoft product and service names are trademarks of Microsoft Corporation.
