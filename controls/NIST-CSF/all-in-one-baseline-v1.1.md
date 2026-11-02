VeritasRiskEngine – NIST CSF 2.0 Controls
All-in-One Advanced Specification
Scope: Autonomous AI Agents + Edge Critical Infrastructure
Version: 1.1 (Expanded Condensed)
Date: 2026-11-01
Status: Auditable Baseline + Detailed Controls

Purpose & Scope

This document is the single-source advanced control baseline for the VeritasRiskEngine. It maps the NIST Cybersecurity Framework (CSF) 2.0 to the operational realities of autonomous AI agents operating on or interacting with edge critical infrastructure.

It covers:

Machine-to-machine (M2M) interactions

Agent goal execution, tool use, and intent integrity

Edge-node integrity, firmware, and continuous health

Human-in-the-loop (HITL) requirements

Independent telemetry and continuous verification

Hierarchical, firmware-aware, bounce-resilient kill switches

Daily adversarial testing and residual-risk closure

All higher-level profiles, risk engines, and overlays in the repository must remain consistent with the requirements defined here.

Core Operational Guardrails (Cross-Cutting – Non-Negotiable)

These rules apply to every Function, Category, agent, and edge node.

2.1 Human-in-the-Loop (HITL) Validation

Any agent action that can produce irreversible effects on critical infrastructure, safety systems, or high-value assets must support a configurable HITL checkpoint.

HITL thresholds are defined by risk tier and autonomy level.

Bypass is permitted only under pre-authorized emergency playbooks and must be fully logged and reviewed post-event.

2.2 Independent Telemetry Logging

All agent decisions, tool invocations, goal updates, and edge-node state changes must emit structured, timestamped, immutable telemetry.

Telemetry is written to an independent plane that the agent runtime cannot modify, suppress, or delete.

Minimum requirements: tamper-evident storage and cryptographic chaining.

2.3 Continuous Verification of Machine-to-Machine Interactions

Every M2M interaction (agent-to-agent, agent-to-edge, edge-to-edge) must be continuously verifiable.

Verification includes: identity authenticity, authorization scope, intent/goal consistency, and behavioral baseline adherence.

Deviations trigger automated containment or escalation.

2.4 Edge-Node Health as First-Class Control

Edge-node health (integrity, configuration drift, resource anomalies, cryptographic posture, behavioral baseline, kill-switch readiness) is a primary security observable.

Health telemetry feeds risk scoring, Detect functions, and kill-switch decisions in real time.

CSF 2.0 Function Mappings

3.1 GOVERN (GV)

Define autonomy tiers, risk appetite for agent actions, and edge-node criticality classifications. Explicitly document which decisions require HITL.

Maintain temporal risk horizons and capability-jump considerations. Risk strategy must include daily adversarial testing.

Assign clear ownership for agent operators, edge-node owners, override authorities, and telemetry plane administrators.

Enforce signed goal mandates. Policy must require independent telemetry and prohibit agent self-modification of logging or kill-switch paths.

Oversight receives regular metrics on agent autonomy usage, edge-health status, HITL invocation rates, and residual exploit findings.

Require Model Bills of Materials (MBOM), data lineage, and PQC-agile credentialing for all agents and edge software.

3.2 IDENTIFY (ID)

Maintain a living inventory of all agents (versions, goal scopes, tool permissions) and edge nodes (hardware, firmware, cryptographic posture, health baseline).

Perform entanglement-aware risk assessments that capture cascade potential across domains, including agent intent-drift risk and edge-node compromise paths.

Feed daily adversarial test results and edge-health anomalies into continuous improvement of agent policies and node configurations.

Map agent decision paths and edge nodes to critical business/operational functions and safety outcomes.

3.3 PROTECT (PR)

Every agent must possess a distinct, cryptographically verifiable identity separate from human and service accounts. Credentials are short-lived and goal-bound. Edge nodes enforce mutual authentication for M2M.

Personnel who authorize or oversee agents must be trained on HITL thresholds, intent verification, and edge-health interpretation.

Protect agent memory, context stores, and training artifacts with lifetime-aware cryptographic controls.

Harden edge nodes, enforce configuration baselines, maintain cryptographic agility, and perform continuous health monitoring.

Implement daily automated adversarial testing of agents and edge nodes. Results are reported as residual-risk sets.

Edge-node maintenance and agent updates must preserve telemetry continuity and kill-switch readiness.

Deploy the hierarchical kill-switch architecture defined in Section 4. Kill paths must be independent of the agent runtime where feasible.

Enforce least-privilege tool use and data access. Dynamic scope reduction based on observed behavior is required.

3.4 DETECT (DE)

Detect behavioral drift from agent baselines, intent/goal divergence, edge-health anomalies, and anomalous M2M patterns.

Stream agent actions, tool calls, goal updates, and full edge-health tensors to the independent telemetry plane. Monitoring must be agent-independent.

Detection logic must support real-time correlation across agent behavior and edge-node state. False-negative tolerance is defined by risk tier.

3.5 RESPOND (RS)

Maintain playbooks for agent quarantine, goal revocation, edge-node isolation, firmware interlock activation, and multi-domain cascade containment. Include HITL escalation paths.

Notify designated authorities and log all response actions on the independent telemetry plane.

Analyze root cause including intent drift, edge compromise vectors, and M2M interaction failures.

Activate hierarchical kill switches and containment actions. Prefer reversible containment before permanent retirement.

Update agent policies, edge baselines, and detection rules from response lessons.

3.6 RECOVER (RC)

Define recovery paths that include agent re-alignment, edge-node rebuild from known-good state, and verification of restored health tensors (including firmware measurements).

Capture recovery metrics (time-to-restore, residual risk after recovery) and feed into Identify and Protect improvements.

Communicate recovery status and any residual limitations to stakeholders.

Five-Strata Kill-Switch Hierarchy (Detailed)

The kill-switch is a strict graded partial order. Lower strata are attempted first. Higher strata remain functional even if the agent runtime or primary OS is fully compromised. All activations are logged to the independent telemetry plane.

Stratum 1 — Soft Goal Revocation

Mechanism: Cryptographically signed goal-mandate update that nullifies or restricts the agent's current objective.

Scope: Agent decision / planning layer only.

Reversibility: Fully reversible.

Independence: Low (still travels through agent-facing channels).

Firmware Impact: None.

Key Controls: Mandate signing keys held outside agent runtime. Agent verifies signature, version, and anti-rollback counters. Full cryptographic logging.

NIST Mapping: SP 800-53 AC-3, AC-6, IA-2, IA-5, AU-2, AU-3, SI-7; SP 800-82 command validation concepts.

Stratum 2 — Middleware / Runtime Freeze

Mechanism: Agent-control-plane hooks that suspend tool invocation, memory writes, and external side-effects while preserving internal state for diagnostics.

Scope: Agent execution environment / container / process group.

Reversibility: High.

Independence: Medium.

Firmware Impact: None.

Key Controls: Hooks enforced by a component not modifiable by the agent. Freeze state externally observable. Timeout + automatic escalation if not acknowledged.

NIST Mapping: SP 800-53 AC-3, AC-4, SI-4, SI-7, IR-4.

Stratum 3 — Edge-Node Quarantine (OS / Network Layer)

Mechanism: Network and process isolation driven by the independent health monitor.

Scope: Entire edge node OS instance, containers, and network interfaces (except protected management/telemetry channels).

Reversibility: Medium (requires re-attestation).

Independence: High.

Firmware Impact: Indirect (prevents further firmware interaction from a compromised OS).

Key Controls: Decision made by health monitor independent of agent and primary OS. Deny-all network policy except telemetry and out-of-band management. Process/cgroup isolation. Health tensor continues reporting.

NIST Mapping: SP 800-53 AC-4, SC-7, SI-4, IR-4, CM-7; SP 800-82 network segmentation and zone controls.

Stratum 4 — Firmware / Hardware Interlock (Primary Firmware Kill Path)

Mechanism: Actuation at firmware, BMC, secure element, independent microcontroller, or hardware-relay level.

Scope: Firmware execution, boot path, hardware outputs, or power/isolation relays.

Reversibility: Low to medium (may require physical or out-of-band reset).

Independence: Very High (must not share compute, memory, or primary network with agent runtime or main OS).

Firmware-Specific Requirements:

Secure / measured boot must remain enforceable.

Authenticated out-of-band command channel or hardware interlock that can halt execution, force known-good boot, or open isolation relays.

Anti-rollback and signed firmware update mechanisms must be intact and independently verifiable.

Interlock status readable by the independent telemetry plane.

Periodic readiness testing required (included in daily adversarial closure and health tensor).

NIST Mapping: SP 800-53 SI-7, SA-10, SA-11, CM-7, SC-7, IR-4, CP-10; SP 800-82 safe-state requirements; SP 800-193 (Platform Firmware Resiliency) principles.

Stratum 5 — Cascading Multi-Domain Isolation

Mechanism: Coordinated activation across pre-computed entanglement cuts spanning multiple agents, edge nodes, and infrastructure domains.

Scope: Multi-node, multi-domain.

Reversibility: Low.

Independence: Highest.

Firmware Impact: Triggers Stratum 4 interlocks on all nodes in the cascade set.

Key Controls: Pre-authorized cascade playbooks derived from entanglement density maps. Cross-domain consensus or designated cascade authority. Full correlated telemetry. Explicit inclusion of firmware interlock status for every node.

NIST Mapping: SP 800-53 IR-4, IR-8, CP-2, CP-10, PM-9; multi-system coordination in SP 800-82.

Activation Summary:
Stratum 1: Auto-Activate = Yes | HITL Required = No | Firmware Level = No
Stratum 2: Auto-Activate = Yes | HITL Required = No | Firmware Level = No
Stratum 3: Auto-Activate = Yes (on health-tensor triggers) | HITL Required = Configurable | Firmware Level = Indirect
Stratum 4: Auto-Activate = Limited (pre-authorized safety cases only) | HITL Required = Yes | Firmware Level = Yes (Primary)
Stratum 5: Auto-Activate = No | HITL Required = Yes (explicit cascade authority) | Firmware Level = Yes

Bounce Recovery Process

Collect final health tensor (including firmware integrity measurements) and residual risk indicators.

Decide: resume at reduced autonomy, force known-good firmware boot + rebuild, or permanently retire.

Re-attest identity, firmware measurements (secure/measured boot logs), cryptographic posture, and behavioral baseline.

Log the entire recovery path as a first-class audit object.

Edge-Node Health Controls

Health Tensor (Minimum Required Dimensions)
Dimension: Integrity | Description: Measured deviation from known-good firmware, OS, and configuration baselines | Criticality: High
Dimension: Configuration Drift | Description: Unauthorized or unexpected changes to security-relevant settings | Criticality: High
Dimension: Cryptographic Posture | Description: Algorithm suite, key ages, PQC readiness indicators, certificate status | Criticality: High
Dimension: Resource Anomalies | Description: CPU, memory, storage, network, and process deviations from baseline | Criticality: Medium
Dimension: Behavioral Baseline | Description: Process, network, and agent-interaction patterns relative to learned normal | Criticality: High
Dimension: Telemetry Integrity | Description: Evidence that health and agent telemetry channels remain uncompromised | Criticality: Critical
Dimension: Kill-Switch Readiness | Description: Status and last successful test of applicable kill-switch strata | Criticality: High

The tensor is versioned, timestamped, and cryptographically protected before transmission to the independent telemetry plane.

Continuous Monitoring Rules

Collection interval is risk-tier dependent (near-real-time for critical nodes; maximum 5 minutes for any production node).

Collection and reporting must function even when the primary agent runtime is frozen or quarantined.

The monitoring component itself is part of the trusted computing base and subject to integrity verification.

Integrity & Failure Handling

Known-good baselines stored and verified using mechanisms resistant to agent compromise (secure boot, measured boot, independent secure element, or equivalent).

Any detected integrity failure or high-severity drift automatically raises an anomaly and may trigger Stratum 3 or 4.

Loss of health telemetry is treated as a high-severity event and results in quarantine pending investigation.

Health-tensor forgery or suppression attempts are treated as active compromise indicators.

Integration Points

Feeds Detect (DE.AE / DE.CM)

Directly informs Stratum 3 and higher kill-switch decisions

Explicitly tested during daily adversarial closure

Required for recovery verification before return to service

Aggregate metrics reported to oversight (Govern)

Daily Adversarial Closure Procedure

Purpose
Every 24 hours the system must actively test the set of known and hypothesized exploits against agents and edge nodes, quantify residual risk, and report findings to the independent telemetry plane.

Scope of Testing
Agents:
Goal-mandate integrity and revocation response, tool-use authorization boundaries, memory/context store integrity, identity and credential handling, behavioral baseline adherence under adversarial input, kill-switch responsiveness (Strata 1–3).

Edge Nodes:
Configuration and firmware integrity, cryptographic posture (including PQC indicators), resource and process anomalies, network exposure and M2M authentication, health-tensor reporting integrity, quarantine and hardware interlock responsiveness.

Cross-Cutting:
M2M interaction verification under adversarial conditions and telemetry plane integrity (agents must not be able to suppress findings).

Daily Procedure (Normative)

Pre-Execution: Refresh the exploit catalog from authoritative sources and internal threat intelligence. Select the test set (critical nodes/agents prioritized; coverage rotated). Verify that the independent telemetry plane and health monitors are operational.

Execution: Launch automated, instrumented adversarial probes in controlled environments or against production nodes under strict safety constraints. Record probe type, target, expected vs. observed behavior, detection latency, containment action, and final residual state. Escalate immediately if a live compromise indicator is observed.

Post-Execution & Reporting: Compute the residual-risk set (exploits not fully prevented or detected, or for which containment was incomplete). Generate a structured report containing coverage summary, detection/containment metrics, residual-risk set, and recommended mitigations. Publish to the independent telemetry plane within 24 hours of cycle start. Notify designated oversight roles of any high-severity residuals.

Feedback: Residual findings automatically generate tasks in the improvement pipeline. Update agent policies, edge baselines, and detection rules as required.

Safety Requirements

Production testing must use non-destructive or tightly scoped probes unless explicit authorization and rollback capability exist.

High-risk probes are first executed in staging or shadow environments that mirror production.

Kill-switch and quarantine capabilities must remain available throughout testing.

Required Evidence Objects

Daily residual-risk set

Coverage percentage (agents and edge nodes)

Mean time to detect / mean time to contain

Number and aging of high-severity residuals

Implementation Notes

All controls are expressed as outcomes that can be evidenced through telemetry, configuration, and audit logs.

The independent telemetry plane is a foundational architectural requirement.

Daily adversarial closure generates measurable residual risk that feeds Identify, Protect, and Govern.

Kill-switch activations and HITL events are first-class audit objects.

This specification is designed to be extended by higher-level profiles (sector-specific, capability-jump ready, multi-domain, etc.) while remaining the auditable foundation.

NIST Alignment Summary

Area: Overall Framework | Primary References: NIST CSF 2.0
Area: Access Control & Identity | Primary References: SP 800-53 AC & IA families
Area: System & Information Integrity | Primary References: SP 800-53 SI-7, SI-4; SP 800-193
Area: Incident Response | Primary References: SP 800-53 IR family
Area: Configuration & Safe State | Primary References: SP 800-53 CM family; SP 800-82
Area: Contingency / Recovery | Primary References: SP 800-53 CP family
Area: OT / Edge Isolation | Primary References: SP 800-82
Area: Supply Chain & Firmware | Primary References: SP 800-161, SP 800-53 SA family

End of All-in-One Specification
This document constitutes the complete condensed-yet-detailed control baseline for autonomous AI agents and edge critical infrastructure under the VeritasRiskEngine.
