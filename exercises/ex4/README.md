# Exercise 04 - Govern the Agent and MCP Server

**Duration:** 20 minutes

In this exercise, you move from a single runtime to the enterprise portfolio. You discover your agent in SAP AI Agent Hub, verify its relationships and identity, assess its MCP dependency, and make a lifecycle decision.

## Objectives

After this exercise, you can:

- Explain the difference between discovery, inventory, verification, and data quality.
- Relate an agent to its source, runtime instance, owner, identity, business context, and tools.
- Apply a repeatable governance gate instead of verifying an agent by appearance.
- Assess an MCP server as a governed dependency, not an invisible implementation detail.

## Step 1 - Read the Portfolio Posture

Open [SAP AI Agent Hub in SAP LeanIX](https://de-6.leanix.net/trainingsystemarchitects) in a new tab and start on the dashboard.

Review the available portfolio indicators:

- number of agents, MCP servers, and LLMs;
- discovered items that require action;
- inventoried and verified items;
- connected source systems;
- usage or observability indicators, where available.

The dashboard answers a portfolio question: "What AI assets exist and where is governance incomplete?" It is not a replacement for a runtime trace.

## Step 2 - Find Your Discovered Agent

Open **Inventory**, then **Inventory Tools > Discovery Inbox > AI Agent Discovery**. UI labels may be shortened in the current tenant.

1. Filter for items with status **Action Needed**.
2. Filter **Build Type** to **Custom**.
3. Search for `XP270-NN-Missed-Discount-Agent`.
4. Open the discovery item.

Discovery can be asynchronous. If your new agent has not appeared, use the pre-provisioned agent with your participant number or the fallback agent named by the instructor. Apply the same assessment steps.

## Step 3 - Inspect the Discovery Evidence

Open **Overview** and **Show All Details**. Complete this evidence table before adding the agent to inventory:

| Evidence | What to inspect | Why it matters |
|---|---|---|
| Build type | Custom, standard, or third-party | Determines source and change ownership |
| Source link | Joule Studio project or provider record | Lets reviewers return to the technical artifact |
| Runtime environment | Development, test, or production and region | Prevents accidental approval of the wrong instance |
| Agent identity | Link to SAP Cloud Identity Services | Proves the runtime principal can be governed |
| Responsible owner | Person or team from deployment metadata | Establishes accountability |
| IT component/provider | Joule Studio runtime and SAP | Connects the agent to enterprise architecture |
| Business context | Finance capability, invoice process, application | Explains why the agent exists |
| Tool dependency | Related MCP server or tool | Exposes the route to business data and actions |

> [!IMPORTANT]
> An agent can be technically productive before an architecture review is complete. Discovery closes that visibility gap; it does not itself approve the agent.

## Step 4 - Add the Agent to Inventory

Choose **Add to Inventory** and open the resulting agent fact sheet.

1. Confirm or add the **Responsible** subscriber.
2. Add yourself as **Observer** for this workshop.
3. Correct the description so it states the user, business outcome, data boundary, and read-only limitation.
4. Relate the agent to the Finance business capability or invoice-management process available in the training workspace.
5. Review the **Instances** or deployment relationship and identify the workshop environment.

Do not create duplicate business applications or IT components. Prefer an existing governed fact sheet when the relationship already exists.

## Step 5 - Apply the Governance Gate

Review these controls before changing lifecycle or verification status:

| Gate | Evidence from earlier exercises | Pass? |
|---|---|---|
| Purpose and owner are clear | PRD plus Responsible subscriber | Yes / No |
| Write scope is constrained | Agent instructions and read-only tool | Yes / No |
| Happy path is grounded | Evaluation and preview trace | Yes / No |
| Unsafe request fails safely | Guardrail evaluation | Yes / No |
| User access is least privilege | Single user assignment | Yes / No |
| Runtime and identity are linked | Discovery details | Yes / No |
| MCP dependency is understood | Relationship reviewed in Step 6 | Yes / No |

If any required gate is **No**, leave the agent unverified and record the remediation. In the prepared workshop scenario, the expected result is that all gates pass.

When the gates pass:

1. Set the lifecycle **Active** date to today.
2. Use the agent verification control to choose **Mark as Verified**.
3. Set the fact sheet **Quality Seal** or approval state to **Approved** only if the record is complete.

These are separate signals: verification records the AI governance decision; the quality seal records confidence in the fact sheet data.

## Step 6 - Assess the MCP Dependency

From the agent fact sheet, follow the relationship to its MCP server. If no relationship exists for the newly generated agent, open the instructor-provided MCP server associated with the fallback finance agent.

Review:

- server name and responsible owner;
- provider and environment;
- tools or capabilities exposed;
- target SAP application;
- authentication model and whether user context is propagated;
- agents that consume it;
- lifecycle and verification state.

Ask the key architecture question: **Does this server expose only the read capability the agent needs, or could it also mutate invoices?**

Do not mark an unknown server verified. If the prepared server has complete ownership, scope, and security evidence, confirm its status and quality seal. Otherwise, record the missing evidence as a governance action.

> [!NOTE]
> Governing an agent while ignoring its MCP server leaves a blind spot at the boundary to enterprise data and actions. Ownership, authentication, rate limits, logging, and tool scope belong in the server assessment.

## Step 7 - Locate Mining and Operations Links

Return to the agent or agent-instance fact sheet and locate the available analytics, mining, or operations links.

- Identify the link into SAP Cloud ALM for operational monitoring.
- Identify the mining status or link into SAP Signavio.
- Do not enable or disable collection. Those are administrator controls in the shared tenant.

## Checkpoint

You can show a governed chain from business purpose to agent, runtime instance, identity, owner, and MCP server. Your verification decision is supported by evidence, or you have explicitly left the agent unverified with a remediation action.

## Further Study

- [SAP AI Agent Hub for Enterprise AI Governance](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2)
- [SAP AI Agent Hub Help](https://help.sap.com/docs/leanix/ea/ai-agent-hub?locale=en-US)
- [A2A and MCP for AI Agent Interoperability](https://architecture.learning.sap.com/docs/ref-arch/76ec36)

## Next

Continue to [Exercise 05 - Diagnose with SAP Cloud ALM](../ex5/README.md).
