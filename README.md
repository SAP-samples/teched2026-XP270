# XP270 - Get Hands-On: Build, Orchestrate, and Monitor Your AI Agents

## Description

This repository contains the material for the 120-minute SAP TechEd 2026 session **XP270 - Get Hands-On: Build, Orchestrate, and Monitor Your AI Agents**.
This session will walk you through an agent life-cycle on SAP Business AI Platform.

## What You Will Do

You will take one finance agent through an enterprise lifecycle on SAP Business AI Platform:

1. Design, generate, test, evaluate, and deploy a custom agent in SAP Joule Studio.
2. Experience a denied production invocation and grant the user access in SAP Cloud Identity Services.
3. Run the custom agent and an SAP standard agent through the governed runtime.
4. Discover the agent, its identity, runtime, and MCP dependency in SAP AI Agent Hub.
5. Apply a lifecycle and verification decision in SAP LeanIX.
6. Diagnose a slow or failed execution in SAP Cloud ALM.
7. Analyze behavior and process variants with SAP Signavio Process Intelligence.

The workshop is based on the **Agentic AI & AI Agents on SAP Business AI Platform**, **AI Agent Identity**, **AI Agent Behavior Mining**, and **SAP AI Agent Hub** reference architectures from the SAP Architecture Center.

![Agentic AI and AI agents architecture](images/agentic-ai-ai-agents-diagram.png)

## Business Scenario

You work in the AI Governance Center of Excellence at **GlobalFlex AG**, a manufacturer running SAP S/4HANA. Accounts Payable wants an agent that identifies unmatched supplier invoices whose early-payment discounts are at risk.

Your team must deliver more than a working prototype. The agent must be grounded in authorized SAP data, read-only by design, assigned to approved users, discoverable in the enterprise architecture, observable in production, and supported by evidence for improvement or retirement.

You will work in two roles:

| Role | Primary questions |
|---|---|
| SAP Developer | Does the agent call the right tool, return grounded results, fail safely, and expose useful traces? |
| SAP Architect | Who owns it, what can it access, where is policy enforced, and what evidence supports activation? |

## Learning Objectives

After completing the workshop, you can:

- Apply intent-based development from requirements through evaluation and deployment.
- Explain why deployment and user authorization are separate controls.
- Trace identity and access decisions across SAP Cloud Identity Services.
- Relate an agent to its owner, runtime, business context, identity, and MCP server in SAP AI Agent Hub.
- Distinguish build-time traces, operational monitoring in SAP Cloud ALM.
- Use trace and evaluation evidence to recommend remediation, activation, or decommissioning.

## Agenda

| Time | Exercise | Outcome |
|---:|---|---|
| 10 min | [00 - Get Ready](exercises/ex0/README.md) | Verify access and define your workshop identifiers |
| 10 min | [01 - Map the Architecture](exercises/ex1/README.md) | Trace the request, identity, governance, and telemetry paths |
| 35 min | [02 - Build and Deploy](exercises/ex2/README.md) | Create, evaluate, trace, and deploy the custom agent |
| 15 min | [03 - Enforce Access](exercises/ex3/README.md) | Diagnose a denial, assign access, and execute two agents |
| 20 min | [04 - Govern the Agent and MCP Server](exercises/ex4/README.md) | Discover dependencies and make a verification decision |
| 15 min | [05 - Diagnose with SAP Cloud ALM](exercises/ex5/README.md) | Find the slow or failing step in one session |
| 10 min | [06 - Mine Behavior with SAP Signavio](exercises/ex6/README.md) | Compare variants and identify an improvement action |
| 5 min | [07 - Close the Control Loop](exercises/ex7/README.md) | Produce an evidence-based architecture decision |
| **120 min** | | |

The core path is deliberately linear. Keep the same participant number, agent name, and trace/session evidence throughout.

## Prerequisites

- Basic understanding of APIs, authentication, and AI agents.
- A modern browser. No local development tools are required.
- An assigned workshop user and participant number.

## Start

Continue to [Exercise 00 - Get Ready](exercises/ex0/README.md).

## Related Sessions

- [XP268 - Govern the agent economy: Secure A2A using SAP's agent gateway](https://github.com/SAP-samples/teched2026-XP268)
- [AD163 - Discover insights with Process Consulting Agent](https://github.com/SAP-samples/teched2026-AD163)
- [BT161 - SAP AI Agent Hub: AI Governance Workshop from Discovery to Decommissioning](https://github.com/SAP-samples/teched2026-BT161)

## Support

Support for this content is available during the scheduled SAP TechEd session. Outside the session, use the repository issue tracker.

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing changes.

## Code of Conduct

All participants and contributors must follow the [SAP Open Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## License

Copyright (2026) SAP SE or an SAP affiliate company and XP270 contributors. See [LICENSE](LICENSE) for copyright and license information.
