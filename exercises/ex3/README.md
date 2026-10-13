# Exercise 03 - Govern your agent in the SAP LeanIX - AI Agent Hub

Now that we understand our agent and can see it is healthy in Joule Studio, we switch hats. Joule Studio only sees the agents it runs; as the AI Governance Center of Excellence, we need the whole picture — every agent, MCP server, and LLM across the landscape — and a way to formally approve each one for production. That is what the **SAP LeanIX - AI Agent Hub** gives us.

At the end of this exercise, you'll have successfully taken your finance agent from a raw discovery all the way to a verified, governed inventory record.

## Background

The AI Agent Hub automatically discovers agents from connected systems: standard SAP agents, custom agents deployed on Joule Studio, and third-party agents from platforms such as Microsoft Entra ID, Google Cloud, and AWS Bedrock. Whatever its origin, every agent goes through the same review-and-approve process before it enters the governed inventory. Your Joule Studio finance agent has been discovered and is waiting for you.

> [!NOTE]
> Everyone shares one LeanIX workspace, so use your participant number (`XP270-0NN`) to find *your* agent throughout this exercise.

## Step 1 — Orient yourself in the AI Agent Hub

👉 In **SAP LeanIX**, open the **AI Agent Hub Dashboard** and read the overview: total agents, MCP servers, and LLMs; the **Discovery → Inventory → Verified** pipeline; and the **Connected systems** feeding discovery data in — including Joule Studio, SAP Cloud ALM, and Signavio.

> [!NOTE]
> **What you are seeing:** a real-time governance posture — how many agents exist, how many are verified, and how much AI activity is happening in your landscape right now. The **Inventory** holds everything known to the system; the **AI Agent Discovery Inbox** surfaces the items that need your attention.

## Step 2 — Find your agent in the Discovery Inbox

👉 Navigate to **Inventory → Inventory Tools** *(top right)* **→ Discovery Inbox → AI Agent Discovery**.

👉 Apply the filter **Status: Action Needed**, add the **Build Type: Custom** filter, then search for your participant number to find your agent.

👉 Open your discovery item and review the **Overview** — what the agent claims to do, when it first appeared, its **Build Type** (Custom), and the **Discovered Fact Sheets**: the IT component (the Joule Studio runtime), the provider (SAP), and **any MCP servers the agent uses**.

![The agent's discovery record in the AI Agent Hub](images/03_discovery-inbox.png)

👉 Click **Show all details** and note two links in particular:

- the **Joule Studio link**, which opens the agent project you explored in Exercise 2;
- the **Cloud Identity Services link**, which shows the agent's **identity record** — confirming the agent has a registered identity, so authentication, access policies, and user authorizations can be managed there.

> [!IMPORTANT]
> **Why this matters:** the Details page shows whether the agent runs in a **productive** environment. If it does, real users may already be interacting with it — potentially against live SAP S/4HANA data — before any governance review has taken place. That is exactly the gap we are closing.

## Step 3 — Add your agent to the governed inventory

👉 Click **Add to Inventory**. The agent becomes part of the governed inventory and its status changes to **Unverified**. Open the newly created fact sheet.

> [!NOTE]
> The person who deployed the agent is automatically assigned as the **Responsible** subscriber, pulled from the deployment metadata. As the EA team, your role is **Observer** — you'll set that next.

## Step 4 — Complete the governance profile

Subscriptions define who is accountable for the agent and who gets notified when it changes.

👉 In the fact sheet's **Subscriptions** section, add **yourself as Observer**. Confirm the **Responsible** subscriber (the deploying team / business owner) is set.

👉 Check the **Description** is accurate — not a generic template. If it is thin, use LeanIX's built-in **AI-generate** option (the sparkle icon in edit mode) to improve it.

> [!TIP]
> Fields such as **AI Risk**, **AI Model**, and **Business Criticality** usually come from the agent's business owner. In a full governance process you would collect them with a survey before verifying — in this session your trainer has pre-populated them so we can proceed to verification.

## Step 5 — Set the lifecycle to Active

Before verifying, record where the agent sits in its lifespan. Every fact sheet has a **Lifecycle** field with five date-driven phases:

| Phase | Meaning |
|-------|---------|
| **Plan** | Being considered or designed — not built yet |
| **Phase In** | Being built, acquired, or rolled out |
| **Active** | Productive and in active use |
| **Phase Out** | Being retired or replaced, but still partly in use |
| **End of Life** | No longer in use |

👉 Open the **Lifecycle** field in the fact sheet header, set the **Active** phase to **today's** date, and **Save**. The header now shows the current phase as **Active**.

> [!NOTE]
> **Why this matters:** the lifecycle is date-driven — LeanIX derives the current phase from the dates you set. Marking the agent Active means it is productive and approved for use, which is what you are about to confirm with verification.

## Step 6 — Verify the agent

Verification is the governance decision point: marking an agent verified formally approves it for production use in your organization.

👉 In the fact sheet header, click the **Verification Badge** and select **Mark as Verified**. The badge updates to **Agent Verified**.

👉 Then set the **Quality Seal** (the **Approval State** indicator) to **Approved**.

> [!IMPORTANT]
> These are two separate signals. The **Verification Badge** is specific to agents, MCP servers, and LLMs — it means *reviewed and approved to run productively* (the AI governance signal). The **Quality Seal** applies to all LeanIX fact sheets — it means *the data on this record meets your data-quality standard*. Both should be set.

## Summary

Your finance agent is now a fully governed, verified inventory record: discovered, promoted to the inventory, profiled with the right subscribers, placed in its lifecycle, and formally approved for production — with an auditable history of every action in the **Last Updated** tab. In the next exercise we'll turn to how its behaviour is observed in production through SAP Cloud ALM.

## Further Study

* [AI Agent Discovery (SAP Help Portal)](https://help.sap.com/docs/LEANIX)
* [AI Agent Hub (reference architecture)](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2)

## Next

Continue to 👉 [Exercise 04 - Observe your agent in SAP Cloud ALM](../ex4/README.md)
