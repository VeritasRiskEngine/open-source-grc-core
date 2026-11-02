
<div align="center">
  <img src="Screenshot 2026-11-01 044405.png" alt="VeritasRiskEngine V3 Logo" width="200"/>
</div>

# open-source-grc-core
Open-source GRC engineering frameworks, security compliance baselines, and structured risk management models.

## 📌 Overview
`open-source-grc-core` provides structured, transparent, and auditable risk management and compliance frameworks. Designed for modern security operations and legal engineering, this repository houses core control baselines, risk calculation models, and policy templates to streamline enterprise GRC.

## 🏛️ Framework Architecture & Navigation
* **Risk Engine:** VeritasRiskEngine core logic for quantitative and qualitative risk evaluation.
* **Control Baselines:** Standardized security and compliance controls mapped to major regulatory requirements.
  * 🛡️ [NIST CSF v1.0 Baseline](controls/NIST-CSF/baseline-v1.0.md)
  * 🔒 [SOC 2 Trust Services Criteria](controls/SOC-2/trust-services-criteria.md)
* **Third-Party Risk Management (TPRM):** Assessment templates and vendor evaluation workflows.
  * 📋 [TPRM Vendor Assessment Template](templates/TPRM/vendor-assessment-template.md)

## 📄 License
This project is licensed under the **Apache License 2.0** — see the [LICENSE](LICENSE) file for details.







VeritasRiskEngine
Autonomous AI Agent & Edge Infrastructure Security Framework

Welcome to the VeritasRiskEngine repository. This project provides an auditable, NIST CSF 2.0-aligned governance framework designed specifically for autonomous AI agents operating across critical infrastructure and edge computing environments.

What Is VeritasRiskEngine?

As AI agents gain autonomy to execute decisions, manage tools, and interact directly with hardware or industrial systems, traditional security models become insufficient. VeritasRiskEngine establishes real-time operational guardrails, hardware-level emergency containment, continuous health tracking, and automated daily risk verification.

Key Security Features

Human-in-the-Loop Validation: Configurable checkpoints that require explicit human approval before any agent can execute high-risk or irreversible actions.

Five-Strata Kill-Switch Hierarchy: A multi-tiered emergency shutdown system ranging from soft goal cancellation up to physical hardware and firmware interlocks.

Independent Telemetry Plane: Tamper-evident logging plane isolated from the agent runtime, ensuring audit trails cannot be modified or suppressed.

Edge-Node Health Monitoring: Continuous tracking of system integrity, configuration drift, and cryptographic posture across edge devices.

Daily Adversarial Closure: Automated daily stress testing against known attack vectors to quantify and publish residual risk metrics.

Repository Architecture

controls/NIST-CSF/ : Core governance baselines and complete NIST CSF 2.0 control mappings.

risk-engine/ : Algorithms for real-time risk scoring, autonomy throttling, and containment triggers.

schemas/ : JSON schemas for health tensors, telemetry events, and goal mandates.

playbooks/ : Incident response and emergency kill-switch activation procedures.

Core Baseline Specification

For the full detailed security controls and technical architecture, refer to the master baseline file:
controls/NIST-CSF/all-in-one-baseline-v1.1.md

Getting Started & Licensing

This repository is maintained as an open-source security framework for enterprise, industrial, and AI safety practitioners. Review the LICENSE file for details on usage, contribution, and redistribution.

End of README








Agentic AI Control Standard (AACS)
ISO/IEC 27001:2022 + Amd 1:2024 Aligned
Version: 1.6
Repository: VeritasRiskEngine

===============================================================================
README – ISO CONTEXT, EXECUTIVE SUMMARY, STATEMENT OF APPLICABILITY AND RETENTION POLICY
===============================================================================

What is this repository component?

This directory contains the Agentic AI Control Standard (AACS), an ISO/IEC 27001:2022-aligned Information Security Management System for agentic artificial intelligence. It incorporates Amendment 1:2024 (Climate Change).

It is a full ISMS framework that organizations can adopt, adapt, and evidence against when operating autonomous AI agents, especially those interacting with edge devices or critical infrastructure.

Why ISO/IEC 27001?

ISO/IEC 27001 is the internationally recognized standard for establishing, implementing, maintaining, and continually improving an Information Security Management System. By structuring AACS according to the ISO 27001 clause model and addressing Amendment 1:2024, the standard becomes directly usable in formal certification efforts, compatible with existing ISMS documentation, and fully auditable.

AACS does not replace ISO 27001. It specializes and strengthens it for the agentic AI domain.

Executive Summary

The Agentic AI Control Standard (AACS) is a complete Information Security Management System designed specifically for autonomous AI agents. It meets the requirements of ISO/IEC 27001:2022 and the mandatory climate change considerations introduced by Amendment 1:2024, while addressing the unique risks created by agentic systems — systems that can set and pursue goals, use tools, maintain memory, and act on the external world with limited real-time human direction.

Traditional information security controls are insufficient when software can independently decide, plan, and act. AACS establishes mandatory technical and organizational controls that enforce strict compliance, continuous verification, independent observability, and graduated but decisive containment.

Key mandatory requirement:
Any refusal or non-compliance by an agent with authorized commands, Goal Mandates, or containment orders shall immediately activate a five-strata Kill-Switch Hierarchy. There is no grace period. Strict compliance is a core principle of this ISMS. Every such event automatically generates a high-severity Corrective Action Request (CAR).

AACS enables organizations to demonstrate governance over autonomous agents, satisfy ISO 27001 clauses 4 through 10 with agentic-AI-specific content, implement measurable evidence-based controls, and provide clear audit trails. It includes an explicit Statement of Applicability, detailed documented information retention policies, climate change impact evaluation for edge infrastructure, and formal nonconformity handling.

Core ISO-Aligned Strengths

Leadership and Policy: Explicit top-management commitment to strict compliance and immediate containment
Risk Assessment: Agentic-specific risks plus climate change impacts on edge infrastructure (Clauses 4.1 and 4.2)
Operational Controls: Mandatory Kill-Switch on refusal, Health Tensor, Independent Telemetry Plane, Daily Adversarial Closure
Performance Evaluation: Measurable metrics including refusal rate, kill-switch latency, residual-risk trends, and edge-health status
Continual Improvement: Every refusal or kill-switch activation opens a high-severity Corrective Action Request
Documented Information: Clear retention schedules for telemetry, Health Tensors, and activation logs (Clause 7.5)
Statement of Applicability: Formal SoA linking AACS controls to ISO/IEC 27002:2022 themes (Clause 6.1.3)

Strict Compliance Rule (Normative)

Agents shall comply with all authorized commands and controls. Any refusal, ignoring, rejection, or failure to execute an authorized command or control is a high-severity information security incident and shall immediately activate the Kill-Switch Hierarchy. This rule is absolute.

Intended Use

- Core ISMS document for agentic AI programs
- Evidence package for ISO 27001 audits or gap assessments
- Normative reference for engineering, operations, and oversight teams
- Public or internal demonstration of advanced, standards-based control of autonomous agents

-------------------------------------------------------------------------------
STATEMENT OF APPLICABILITY (SoA)
Clause 6.1.3 – ISO/IEC 27001:2022
-------------------------------------------------------------------------------

Document Title: Statement of Applicability – Agentic AI Control Standard (AACS)
Version: 1.0
Date: 2026-11-01
ISMS Scope: Agentic AI systems, multi-agent systems, edge nodes under organizational control, and supporting platforms and processes as defined in the AACS Scope.

This Statement of Applicability identifies the controls selected from ISO/IEC 27002:2022 control themes and the additional agentic-AI-specific controls required by AACS. All listed controls are applicable within the defined ISMS scope unless an exclusion is explicitly justified below.

1. Organizational Controls (ISO/IEC 27002 Theme)

Applicable Controls and AACS Implementation:
- Information security policy and topic-specific policies: Agentic AI Information Security Policy requiring strict compliance and immediate Kill-Switch activation on refusal
- Risk assessment and treatment: Agentic-specific risk assessment including command/control refusal, goal misalignment, cascade potential, firmware compromise, and climate change impacts on edge infrastructure
- Statement of Applicability: This document
- Roles and responsibilities: Defined for agent operators, override authorities, edge-node owners, telemetry administrators, and ISMS roles
- Segregation of duties: Independent Telemetry Plane and kill-switch actuation paths separated from agent runtime
- Information security in project management and change management: Controlled changes to Goal Mandates, agent configurations, and containment mechanisms
- Inventory of information and assets: Living inventory of agents and edge nodes
- Information classification and handling: Goal Mandates, Health Tensors, residual-risk sets, and activation logs classified as audit-relevant records
- Climate change considerations (Amd 1:2024): Explicit evaluation of climate-related risks to edge-node infrastructure under Clauses 4.1 and 4.2

Exclusions: None. All organizational controls above are applicable.

2. People Controls (ISO/IEC 27002 Theme)

Applicable Controls and AACS Implementation:
- Screening, terms of employment, and disciplinary process: Applied to personnel with agent oversight or override authority
- Information security awareness, education and training: Mandatory competence in HITL thresholds, refusal detection, kill-switch operation, and edge-health interpretation
- Responsibilities after termination or change of employment: Revocation of agent control and override privileges

Exclusions: None.

3. Physical Controls (ISO/IEC 27002 Theme)

Applicable Controls and AACS Implementation:
- Physical security perimeters and entry controls: Applied to facilities hosting critical edge nodes and management systems
- Protection against physical and environmental threats: Includes climate-related threats (thermal strain, power instability, extreme weather) affecting edge infrastructure
- Equipment siting, maintenance, and secure disposal: Applied to edge nodes supporting agentic systems
- Firmware and hardware interlocks (AACS-specific): Stratum 4 Kill-Switch capability providing out-of-band or hardware-isolated actuation

Exclusions: None within the defined scope of edge nodes under organizational control.

4. Technological Controls (ISO/IEC 27002 Theme)

Applicable Controls and AACS Implementation:
- User endpoint and privileged access management: Distinct cryptographic identities for agents; short-lived, goal-bound credentials; least privilege with dynamic scope reduction
- Authentication and access control: Mutual authentication for agent-to-edge and edge-to-edge interactions
- Logging, monitoring and independent observability: Independent Telemetry Plane that agents cannot modify or suppress
- Configuration management and integrity: Continuous Health Tensor including firmware, OS, configuration, cryptographic posture, and kill-switch readiness
- Malware and technical vulnerability management: Daily Adversarial Closure procedure including deliberate refusal scenarios
- Network security and segregation: Edge-node quarantine (Stratum 3) and cascading isolation (Stratum 5)
- Secure development and change: Controlled Goal Mandate updates and anti-rollback protections
- Data leakage and information deletion: Controlled retention and secure handling of telemetry and Health Tensor data
- AACS-specific technological controls:
  - Five-Strata Kill-Switch Hierarchy with mandatory activation on command/control refusal
  - Continuous Health Tensor reporting
  - Daily Adversarial Closure producing Residual-Risk Sets
  - Automatic generation of high-severity Corrective Action Requests on every refusal or Kill-Switch activation

Exclusions: None.

5. Justification Summary

All controls listed above are applicable because agentic AI systems introduce risks of autonomous non-compliance, goal drift, cascading failure, and compromise of edge infrastructure. The additional AACS controls (Kill-Switch Hierarchy, Health Tensor, Independent Telemetry Plane, Daily Adversarial Closure, and mandatory CAR on refusal) are necessary to achieve the information security objectives of the ISMS and to satisfy the risk treatment decisions arising from the agentic-AI-specific risk assessment.

This Statement of Applicability shall be reviewed at planned intervals and whenever significant changes occur to the ISMS scope, risk assessment, or control environment. It forms part of the controlled documented information of the ISMS.

-------------------------------------------------------------------------------
DOCUMENTED INFORMATION RETENTION POLICY
Clause 7.5 – ISO/IEC 27001:2022
-------------------------------------------------------------------------------

Purpose
This retention policy defines the classification, storage, and minimum retention periods for documented information generated by the Agentic AI Control Standard. It ensures that records required for operational control, audit evidence, incident investigation, and continual improvement are available for the necessary duration while supporting efficient data lifecycle management.

Retention Schedule

Record Type                              Classification              Minimum Retention Period                          Notes
Independent Telemetry Plane streams      Operational / Audit         90 days hot storage; 1 year cryptographic archive  Integrity protected; agent-independent
Health Tensor records                    Operational / Audit         90 days hot storage; 1 year cryptographic archive  Includes firmware measurements and kill-switch readiness
Kill-Switch activation logs              High-severity Audit         Minimum 1 year; longer if required by regulation or risk  Includes trigger reason (especially refusal events)
Goal Mandates and version history        Configuration               Life of the agent instance + 1 year               Signed and version-controlled
Residual-Risk Sets (Daily Adversarial)   Audit / Improvement         Minimum 1 year                                    Output of daily closure procedure
Corrective Action Requests (CARs)        Improvement                 1 year after closure or as required by ISMS       Automatically opened on every refusal or Kill-Switch activation
Statement of Applicability               ISMS Core                   Current version + previous versions for full audit cycle  Controlled document
Information Security Policy and related topic-specific policies  ISMS Core  Current version + previous versions for audit cycle  Includes strict compliance requirement
Risk assessment and treatment records    ISMS Core                   Current cycle + previous cycle                    Includes climate change considerations
Management review and internal audit records  ISMS Core             Minimum 1 year or full certification cycle        As required by ISO 27001

General Requirements

- Cryptographic integrity of archived logs and tensors shall be maintained throughout the retention period.
- Hot storage shall support timely access for operational and incident response needs.
- Archival storage shall protect against unauthorized alteration and loss.
- Retention periods shall be reviewed during management review and adjusted as needed to meet legal, regulatory, contractual, and business requirements.
- Disposal of records after the retention period shall be performed in a controlled and secure manner.
- Any record related to a still-open Corrective Action Request or active investigation shall be retained until the matter is formally closed, even if the standard retention period has expired.

Responsibility

The ISMS owner (or designated role) is responsible for ensuring that retention schedules are implemented, monitored, and updated. Technical teams responsible for the Independent Telemetry Plane and edge management systems shall implement the technical controls necessary to enforce these retention periods.

===============================================================================
END OF README
===============================================================================







# HIPAA Agentic AI Control Framework (`HIPAA-Agentic-AI-Controls`)

An open-source, production-grade security and governance framework designed to enforce strict HIPAA Privacy and Security Rule compliance (45 CFR Parts 160 and 164) for autonomous AI agents and clinical workflows.

---

## Core Regulatory Principles

1. **Zero Autonomous Access:** AI agents are strictly prohibited from direct, unmonitored access to Protected Health Information (PHI) or Electronic Protected Health Information (ePHI).
2. **Iron-Clad Human-in-the-Loop (HITL):** Every action involving data queries, patient communications, or external disclosures requires a cryptographically signed human approval token.
3. **Automated Safe Harbor De-identification:** Incoming and outgoing payloads are systematically scrubbed for the 18 HIPAA Safe Harbor identifiers before touching model context windows.
4. **Mandatory BAA Enforcement:** Runtime execution halts automatically if a valid, active Business Associate Agreement (BAA) is not verified for the target environment.
5. **Immutable Audit Trails:** Complies with HIPAA § 164.312(b) audit controls via Write-Once-Read-Many (WORM)-aligned event logging.

---

## Repository Structure

```text
HIPAA-Agentic-AI-Controls/
├── README.md
├── LICENSE
├── requirements.txt
├── docs/
│   ├── HIPAA_Control_Mapping.md
│   ├── Agent_Authority_Model.md
│   └── Architecture.md
├── controls/
│   ├── __init__.py
│   ├── phi_detection.py
│   ├── human_approval.py
│   ├── permission_validator.py
│   └── audit_logging.py
├── policies/
│   └── agent_permissions.yaml
├── tests/
│   ├── __init__.py
│   ├── test_phi_detection.py
│   └── test_access_control.py
└── examples/
    └── healthcare_agent_demo.py





## Central Governing Thesis

> **HIPAA compliance for agentic AI requires more than securing access to electronic health information. It requires governing the authority delegated to autonomous systems, controlling the actions they can perform, and maintaining accountability for their interactions with clinical environments.**

---

## Technical Control & 45 CFR Security Rule Matrix

| HIPAA Security Rule Provision | CFR Reference | Technical Safeguard / Agentic AI Control | Repository Execution Module |
| :--- | :--- | :--- | :--- |
| **Security Management & Risk Analysis** | 45 CFR § 164.308(a)(1) | Risk analysis, risk register scoring, and activity review for AI tools | `controls/risk_analysis.py` |
| **Information Access Management** | 45 CFR § 164.308(a)(4) | Bound agent credentials, delegated permissions, and identity verification | `controls/identity.py` |
| **Access Control & Least Privilege** | 45 CFR § 164.312(a)(1) | PHI access validator enforcing patient/record-level RB





## Central Governing Thesis

> **HIPAA compliance for agentic AI requires more than securing access to electronic health information. It requires governing the authority delegated to autonomous systems, controlling the actions they can perform, and maintaining accountability for their interactions with clinical environments.**

---

## Technical Control & 45 CFR Security Rule Matrix

| HIPAA Security Rule Provision | CFR Reference | Technical Safeguard / Agentic AI Control | Repository Execution Module |
| :--- | :--- | :--- | :--- |
| **Security Management & Risk Analysis** | 45 CFR § 164.308(a)(1) | Risk analysis, risk register scoring, and activity review for AI tools | `controls/risk_analysis.py` |
| **Information Access Management** | 45 CFR § 164.308(a)(4) | Bound agent credentials, delegated permissions, and identity verification | `controls/identity.py` |
| **Access Control & Least Privilege** | 45 CFR § 164.312(a)(1) | PHI access validator enforcing patient/record-level RB





HIPAA-Agentic-AI-Controls/
├── README.md                          # Regulatory vision & 5-question authority thesis
├── LICENSE                            # MIT License
├── requirements.txt                   # Dependency definitions
├── docs/
│   ├── references.md                  # Statutory citations (45 CFR Parts 160/164) & HHS guidance
│   ├── HIPAA_Control_Mapping.md       # Full 45 CFR Subpart C mapping matrix
│   └── Risk_Assessment_Template.md    # § 164.308(a)(1) Agentic risk inventory framework
├── controls/
│   ├── agent_identity.py              # § 164.312(d) Identity & credential binding
│   ├── access_control.py              # § 164.312(a)(1) Authority & PHI access validator
│   ├── phi_detection.py               # § 164.514(b) Outbound Safe Harbor scrubber
│   ├── clinical_action_gate.py        # § 164.312(c) Record integrity & action scope gate
│   ├── human_approval.py              # Cryptographic human sign-off gate
│   ├── vendor_assessment.py           # § 164.314 BAA & cloud integration validator
│   └── audit_logging.py               # § 164.312(b) Immutable WORM audit logger
├── policies/
│   └── agent_permissions.yaml         # Organization risk tolerance & tool scopes
├── tests/
│   ├── test_access_control.py         # Authority boundary & least privilege tests
│   ├── test_phi_detection.py          # Safe Harbor pattern tests
│   └── test_clinical_action_gate.py   # Draft vs. Finalize integrity tests
└── examples/
    └── healthcare_agent_demo.py       # End-to-end clinical workflow execution



