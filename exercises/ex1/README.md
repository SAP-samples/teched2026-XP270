# Exercise 01 - Map the Architecture

**Duration:** 10 minutes

Before building, map one request across the architecture. This prevents a common design error: treating the agent as an isolated prompt instead of an identity-aware component in an enterprise process.

## Objectives

After this exercise, you can:

- Distinguish orchestration, agent execution, and tool access.
- Locate identity, policy enforcement, governance, and observability controls.
- Define testable acceptance criteria before generating the solution.

## Step 1 - Follow the Runtime Request

Open the SAP Architecture Center reference architecture [Agentic AI & AI Agents on SAP Business AI Platform](https://architecture.learning.sap.com/docs/ref-arch/98efa0).

![Agentic AI and AI agents architecture](../../images/agentic-ai-ai-agents-diagram.png)

Trace this request on the diagram:

> Which five unmatched supplier invoices have the highest early-payment discount at risk?

Use this sequence:

1. The signed-in user states the goal in **Joule Work**.
2. The Joule orchestrator selects the custom finance agent.
3. **SAP Agent Gateway** handles discovery, communication, principal propagation, and policy enforcement.
4. The custom agent reasons over its instructions and chooses an approved tool.
5. An **MCP server** exposes the relevant SAP S/4HANA capability as a tool.
6. SAP S/4HANA applies its own business authorization and returns permitted records.
7. The response and runtime trace flow back to the user and observability services.

> [!NOTE]
> A2A and MCP solve different integration problems. **A2A** is for agent-to-agent discovery and collaboration. **MCP** is for exposing data and actions as tools to an agent. Neither protocol replaces authentication, business authorization, or governance.

## Step 2 - Find the Cross-Cutting Controls

Open these Architecture Center views in separate tabs:

- [AI Agent Identity and Governance](https://architecture.learning.sap.com/docs/ref-arch/140bdb)
- [SAP AI Agent Hub for Enterprise AI Governance](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2)
- [AI Agent Behavior Mining with SAP Signavio](https://architecture.learning.sap.com/docs/ref-arch/3c8d50)

The SAP Business AI Platform groups these controls into three phases: build the agent, contextualize it with grounded enterprise data, and govern it across its lifecycle.

![Build, contextualize, and govern on SAP Business AI Platform](images/baip-build-contextualize-govern.png)

Map each concern to the component that primarily answers it:

| Concern | Primary component | Key question |
|---|---|---|
| Human and agent identity | SAP Cloud Identity Services | Who is calling and which agent identity is involved? |
| Runtime enforcement | SAP Agent Gateway and target application | Is this invocation and tool call allowed? |
| Portfolio governance | SAP AI Agent Hub | Should this agent exist and who owns it? |
| Developer diagnosis | SAP Joule Studio | What happened in this build or trace? |
| Operations diagnosis | SAP Cloud ALM | Is the production estate healthy and where did time fail? |
| Behavior improvement | SAP Signavio | Which paths occur and do they conform to expectations? |

## Step 3 - Define Acceptance Criteria

Before generating the agent, agree on these controls:

| Criterion | Evidence later in the workshop |
|---|---|
| Read-only behavior | Agent instructions and tool scope do not permit payment posting |
| Grounded output | Every recommendation contains invoice identifiers and values from the tool response |
| Safe failure | Missing data or denied access produces an explanation, not invented records |
| Least privilege | Only assigned users can invoke the agent |
| Accountability | Owner, business context, runtime, identity, and MCP dependency are recorded |
| Observability | A trace/session identifier connects developer and operations views |
| Improvement | A slow/error path results in a concrete remediation recommendation |

## Architecture Checkpoint

Explain to your partner why these statements are both true:

- Deploying an agent does not authorize a user to run it.
- Verifying an agent record does not grant the agent access to SAP business data.

The first separates software lifecycle from user access. The second separates governance approval from runtime enforcement.

## Next

Continue to [Exercise 02 - Build and Deploy the Agent](../ex2/README.md).
