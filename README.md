
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
