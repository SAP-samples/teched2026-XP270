# Exercise 05 - Discover and govern an MCP server

In Exercise 3 we governed an *agent*. But an agent is only as trustworthy as the tools it calls. Our finance agent reaches SAP S/4HANA through an **MCP server** — and that MCP server is an enterprise asset in its own right, with its own owner, risk, and lifecycle. If we govern the agent but ignore the servers it depends on, we have only done half the job.

At the end of this exercise, you'll have successfully brought an MCP server under governance in the SAP LeanIX AI Agent Hub, the same way you did for your agent.

## Background

The AI Agent Hub treats agents, **MCP servers**, and LLMs as first-class objects in the inventory — each gets its own fact sheet, with the same discovery, verification, and lifecycle mechanics. When your finance agent was discovered in Exercise 3, the **Discovered Fact Sheets** panel already listed the MCP servers it uses. Now we govern one of them directly.

> [!NOTE]
> MCP servers are discovered from connected systems just like agents. Among third-party sources, SAP currently provides automated MCP server discovery via **Microsoft** — so an MCP server registered there surfaces in the same Discovery Inbox you already know.

## Step 1 — Find the MCP server

👉 In the **AI Agent Hub**, open the **Inventory** and filter the type to **MCP Server** to see the MCP servers known to the landscape. Locate the one your finance agent depends on (use your participant number to find yours).

> [!TIP]
> Alternatively, open your agent's fact sheet from Exercise 3 and follow the relationship to its MCP server — the agent-to-tool dependency is itself part of the governed record.

👉 If your MCP server is still sitting in the **AI Agent Discovery Inbox** with status **Action Needed**, open it there and review its **Overview** — what it exposes, where it was discovered, and which agents relate to it.

![An MCP server fact sheet in the AI Agent Hub](images/05_mcp-server.png)

## Step 2 — Add the MCP server to the inventory

👉 Click **Add to Inventory**. The MCP server becomes a governed fact sheet with status **Unverified** — exactly like your agent did.

> [!IMPORTANT]
> **Why this matters:** an MCP server is the doorway between your agents and your SAP backends. Governing it means you have an owner accountable for it, a record of what it connects to, and a verification decision on the record — so an ungoverned tool cannot quietly become the weakest link behind a verified agent.

## Step 3 — Complete the profile and set the lifecycle

👉 In the MCP server's **Subscriptions** section, add yourself as **Observer** and confirm the **Responsible** owner.

👉 Open the **Lifecycle** field and set the **Active** phase to today's date, then **Save** — the same five-phase, date-driven model you used for the agent (Plan, Phase In, Active, Phase Out, End of Life).

## Step 4 — Verify the MCP server

👉 Click the **Verification Badge** and select **Mark as Verified**, then set the **Quality Seal** to **Approved**.

> [!NOTE]
> The **Verification Badge** applies to MCP servers just as it does to agents and LLMs — the same "reviewed and approved to run productively" signal. Your agent and the tool it depends on are now *both* verified, which is what a complete governance picture looks like.

## Step 5 (optional) — Discover a third-party agent

If you have time, see how the same flow handles agents that were never built on SAP.

👉 Back in the **AI Agent Discovery Inbox**, change the **Build Type** filter to show agents discovered from third-party platforms (for example, Microsoft Entra ID, Google Cloud, or AWS Bedrock). Open one and note that it carries the same fields and goes through the same review-and-approve process as your Joule Studio agent.

> [!TIP]
> This is the point of a vendor-agnostic hub: whether an agent or MCP server is SAP-native, custom, or third-party, it is governed through one consistent workflow and lives in one inventory.

## Summary

We've extended governance from the agent to the **MCP server** it depends on — discovering it, adding it to the inventory, profiling it, placing it in its lifecycle, and verifying it — and seen that third-party agents follow the identical workflow. Governance now covers the agent *and* its tools. Next we'll move from metrics and records to actual behaviour, and mine how our agent runs with SAP Signavio.

## Further Study

* [AI Agent Hub (reference architecture)](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2)
* [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)

## Next

Continue to 👉 [Exercise 06 - Observe agent behaviour with SAP Signavio](../ex6/README.md)
