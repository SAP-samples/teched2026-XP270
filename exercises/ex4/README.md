# Exercise 04 - Manage access with SAP Cloud Identity Services

Throughout this session, access has been "governed by your organization's existing authorization model" — but where does that model actually live for an agent? When your finance agent reads SAP S/4HANA data, *whose* permissions apply? The answer sits in **SAP Cloud Identity Services**, and understanding it is what separates an agent that is safe to operate from one that is a liability.

At the end of this exercise, you'll have an understanding of how an agent's identity and authorizations are managed in SAP Cloud Identity Services, and how permissions are enforced at runtime.

## Why agents need their own identity

Back in Exercise 3, the agent's discovery details included a **Cloud Identity Services link** — proof that the agent has a *registered identity*. That identity is what makes authentication, access policies, and user authorizations manageable in one place. An agent that acts on live business data must be as governed as any human user — arguably more so, because it can act faster and at scale.

SAP Cloud Identity Services supports two operational models for how an agent gets its permissions:

| Model | How it works |
|-------|--------------|
| **Agent in user context** | The agent acts on behalf of a signed-in user, constrained by that user's permissions |
| **Autonomous agent** | The agent has its own independent technical identity and its own permissions |

> [!IMPORTANT]
> At runtime, the **effective permission is the intersection of the user's permissions and the agent's permissions**. Neither the user nor the agent can do something the other is not allowed to do. This is the single most important access-control rule to remember when operating agents — it is what keeps an agent from becoming a way to bypass authorizations.

## Step 1 — Open the agents view in Cloud Identity Services

👉 Open **SAP Cloud Identity Services** and navigate to the **agents** administration view.

![Agent identities in SAP Cloud Identity Services](images/07_cis-agents.png)

👉 Locate the identity record for your finance agent (use your participant number). This is the same record the AI Agent Hub linked to in Exercise 3.

## Step 2 — Review the agent's identity and authorizations

👉 Review what the identity record holds: the agent's registered identity, how it authenticates, and the authorizations assigned to it.

👉 Identify which operational model applies to your agent — is it acting in a user's context, or does it have an autonomous technical identity?

> [!TIP]
> Relate this to the **Agent Gateway** from Exercise 1. The Gateway is the governed connection point where these policies are *enforced* at invocation time — authentication, principal propagation, and policy enforcement all happen there. Cloud Identity Services is where the identity and authorizations are *defined*; the Agent Gateway is where they are *applied*.

## Step 3 — Reason about least privilege

👉 Consider the finance agent's job: it reads unmatched invoices and calculates lost discounts. Ask yourself whether its authorizations match that job and no more.

> [!IMPORTANT]
> **Why this matters:** the goal is least privilege. An agent should hold exactly the access its skills require. Because the effective permission is the intersection of user and agent, over-granting either side widens the blast radius if something goes wrong. Operating responsibly at scale means keeping both sides tight.

## Summary

You've seen where an agent's identity truly lives — SAP Cloud Identity Services — the two operational models for granting it permissions, and the rule that governs runtime access: effective permission is the intersection of user and agent, enforced at the Agent Gateway. This is the access-control foundation that all subsequent observability and governance work builds on.

## Further Study

* [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services?locale=en-US)
* [Agentic AI and AI Agents on SAP Business AI Platform (reference architecture)](https://architecture.learning.sap.com/docs/ref-arch/98efa0)

## Next

Continue to 👉 [Exercise 05 - Observe your agent in SAP Cloud ALM](../ex5/README.md)
