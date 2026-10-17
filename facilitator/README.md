# XP270 Facilitator Runbook

This runbook prepares and operates the 120-minute workshop. It is not part of the participant click path.

## Session Contract

- Audience: SAP developers and SAP architects
- Duration: 120 minutes including setup and close
- Core scenario: custom missed-discount analysis agent plus one SAP standard finance agent
- Teaching pattern: participant action, expected result, architectural reason, evidence checkpoint
- Safety model: isolated build identities; shared governance and observability tenants; viewer-only SAP Cloud ALM and SAP Signavio access

## Pacing

| Clock | Exercise | Facilitator cue |
|---:|---|---|
| 00:00-00:10 | Get ready | Resolve access issues immediately; pair blocked attendees |
| 00:10-00:20 | Architecture | Keep this interactive; do not turn it into a lecture |
| 00:20-00:55 | Build and deploy | Announce 15-, 25-, and 32-minute checkpoints |
| 00:55-01:10 | Enforce access | Protect the initial denied invocation; it is the key security moment |
| 01:10-01:30 | Govern | Require the evidence gate before participants verify |
| 01:30-01:45 | Cloud ALM | Use one prepared error/latency session |
| 01:45-01:55 | Signavio | Compare only two variants to stay on time |
| 01:55-02:00 | Decision | Ask two participants to share different decisions |

## Required Participant Roles

| Product | Participant permission | Do not grant |
|---|---|---|
| SAP Joule Studio | Create, test, evaluate, and deploy in workshop environment | Tenant-wide administration |
| SAP Cloud Identity Services | Narrow permission to assign workshop users to workshop agents | Broad identity or policy administration |
| SAP LeanIX | Edit training agent/MCP fact sheets and relationships | Workspace administration |
| SAP Cloud ALM | AI Agent Monitoring viewer | Administrator role or collection configuration |
| SAP Signavio | Process Intelligence analysis viewer | Pipeline, connection, or mining administration |

Cloud ALM expert guidance explicitly recommends viewer-only access. The collection switch is a critical shared-tenant control.

## Landscape Readiness

Complete these checks no later than the day before delivery:

### Joule Studio and Runtime

- Confirm participant users follow the assigned pattern and can open **Develop**.
- Confirm every user can create and deploy an agent without affecting another participant.
- Confirm the SAP S/4HANA invoice-read capability is connected and contains non-sensitive workshop data.
- Run the four evaluation prompts from Exercise 02.
- Confirm a deployed agent is not automatically assigned to its creator, or prepare a restricted fallback agent for the denial step.
- Confirm session and trace IDs are visible after a run.

### SAP Cloud Identity Services

- Confirm workshop agents appear in the **Agents** view after deployment.
- Confirm participants can assign only their own workshop user to their own workshop agent.
- Pre-provision a fallback custom agent and keep one user deliberately unassigned.
- Confirm the standard finance agent's access model and decide whether participants may change it.

### SAP AI Agent Hub

- Confirm discovery from Joule Studio is active and measure normal discovery delay.
- Pre-provision one discovered custom finance agent per cohort or one clearly named fallback.
- Populate owner, business capability, runtime instance, identity link, and MCP relationship.
- Prepare one complete MCP server fact sheet and one missing-control example for discussion.
- Confirm the Cloud ALM and Signavio links or statuses are visible.

### SAP Cloud ALM

- Use a fixed time range containing prepared sessions.
- Prepare one successful and one failed or slow session with a non-trivial execution flow.
- Confirm **Execution Flow** and **Timeline** both render.
- Confirm whether evaluation health is populated. If not, explicitly teach the distinction between missing evaluation telemetry and runtime trace availability.
- Prefer a session with call correctness, task success, output correctness, or compliance evidence.

### SAP Signavio

- Load a Process Intelligence analysis using the Agent Mining value accelerator or current equivalent.
- Confirm filters for agent, tenant/environment, and time range.
- Prepare a frequent successful variant and a slower/error variant.
- Confirm no personal or confidential business data is exposed.
- Do not depend on newly generated workshop traces arriving during the session.

## Fallback Matrix

| Failure | Participant fallback | Teaching outcome preserved |
|---|---|---|
| Agent generation takes too long | Open the pre-provisioned `XP270-NN-Missed-Discount-Agent` and review its requirements/tests | Design review and evaluation |
| Deployment fails | Use the deployed fallback instance with the participant suffix | Identity and lifecycle flow |
| Invocation is already authorized | Use the restricted fallback agent for the denial, then return to the custom agent | Default-deny behavior |
| Discovery is delayed | Use the pre-discovered fallback fact sheet | Relationship-driven governance |
| New telemetry is delayed | Use the prepared Cloud ALM time window and session | Operational diagnosis |
| Evaluation health is blank | Analyze the trace and record missing evaluation telemetry as a finding | Evidence quality and instrumentation |
| Signavio data is unavailable | Use exported screenshots only as a guided fallback and compare the two prepared variants | Behavior-mining reasoning |

## Facilitation Notes

- Pair a developer with an architect where possible. Ask the developer to explain tool and trace evidence; ask the architect to challenge ownership, identity, and lifecycle evidence.
- Do not celebrate a green happy-path test until the unknown-record and write-request tests have also run.
- Do not allow participants to equate **Verified** with runtime authorization. Verification is a governance decision; SAP Agent Gateway and target applications enforce runtime access.
- Ask participants to distinguish facts from hypotheses in Cloud ALM. A long tool span is evidence; "the backend is overloaded" is a hypothesis.
- Keep product boundaries clear: Joule Studio is the builder view, Cloud ALM is the operations view, and Signavio is the cross-execution behavior view.

## Reset After Each Delivery

1. Remove participant user-to-agent assignments that should not persist.
2. Archive or delete participant-generated workshop agents according to tenant policy.
3. Restore fallback agents to unassigned and known-good state.
4. Reset training fact sheet subscriptions, lifecycle dates, verification, and quality seals.
5. Confirm Cloud ALM and Signavio roles remain viewer-only.
6. Check that no screenshots, exports, or notes contain trace payloads or user data.

## Source and Design Traceability

| Workshop area | Primary source |
|---|---|
| Platform components and request path | [Agentic AI & AI Agents](https://architecture.learning.sap.com/docs/ref-arch/98efa0) |
| Intent-based development | [Building AI Agents with SAP Joule Studio](https://architecture.learning.sap.com/docs/ref-arch/219c07) |
| Identity and policy enforcement | [AI Agent Identity](https://architecture.learning.sap.com/docs/ref-arch/140bdb) |
| Discovery and lifecycle governance | [SAP AI Agent Hub](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2) |
| Operational monitoring | [AI Agent Monitoring in SAP Cloud ALM](https://help.sap.com/docs/cloud-alm/applicationhelp/ai-agent-monitoring) |
| Agent execution analysis | [Analyze Agent Execution Performance](https://help.sap.com/docs/signavio-process-intelligence/reference-guide-for-value-accelerators/analyze-agent-execution-performance?c=742fb724) |
| Behavior-mining architecture | [AI Agent Behavior Mining](https://architecture.learning.sap.com/docs/ref-arch/3c8d50) |
| Detailed Agent Gateway setup | XP268 workshop in the neighboring local repository |

The October 2026 colleague walkthroughs informed the relationship-driven SAP LeanIX steps, the SAP Cloud ALM flow/timeline investigation, the separation of runtime trace and evaluation telemetry, viewer-only roles, and the prepared-data fallback strategy.

## Product Evolution

These products and labels are evolving. Validate navigation against current SAP Help and the live TechEd tenant before publishing screenshots. Keep the learning objective stable even when a tab label changes. Forward-looking Architecture Center content must not be represented as generally available unless the live tenant and current product documentation confirm it.
