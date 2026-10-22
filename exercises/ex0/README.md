# Exercise 00 - Get Ready

**Duration:** 10 minutes

In this exercise, you learn the overall architecture of the relevant components and systems on SAP Business AI Platform.Furthermore you verify access to the workshop landscape and define the identifiers you will use in every later exercise.

## Objectives

After this exercise, you can:

- Identify the role of each component / system / product in the end-to-end flow
- Locate your assigned systems and verify system access

## Step 1 - Record Your Workshop Identifiers

Your instructor gives you a two- or three-digit participant number. In the examples below it is written as `NN`.

Record these values locally. Do not put passwords or secrets in this repository.

| Variable | Format | Example |
|---|---|---|
| Participant ID | `NN` | `017` |
| Workshop user | value assigned by instructor | `XP268-017` |
| Custom agent | `XP270-NN-Missed-Discount-Agent` | `XP270-017-Missed-Discount-Agent` |
| Custom solution | `XP270-NN-Finance-Control` | `XP270-017-Finance-Control` |

> [!IMPORTANT]
> The technical workshop user may use the `XP268-NN` pattern even though this session is XP270. Always use the exact user assigned by the instructor.

## Step 2 - Verify System Access

Open each system in a separate browser tab. Use the credentials supplied by your instructor.

| System | Workshop URL | Required access |
|---|---|---|
| SAP Joule Studio | [Open](https://747326606.eu10.sapdas.cloud.sap/) | Create, test, and deploy solutions |
| SAP AI Agent Hub in SAP LeanIX | [Open](https://de-6.leanix.net/trainingsystemarchitects) | Discovery and fact sheet editing |
| SAP Cloud Identity Services | [Open Agents](https://teched02.accounts.ondemand.com/admin/#/agents?global_tenant_id=213a6874-0ba0-4cbc-b896-139abdd080c5) | Workshop agent assignment |
| SAP Signavio | [Open](https://editor.signavio.com/p/hub/home?t=ae8cd097deb64fad81835f4ac2fb9af7) | Process Intelligence viewer |
| SAP Cloud ALM | URL supplied by instructor | AI Agent Monitoring viewer |

Confirm that you reach the expected landing page:

- In Joule Work, you can open **Develop** or **Joule Studio**.
- In SAP LeanIX, you can open **AI Agent Hub** and the inventory.
- In SAP Cloud Identity Services, the **Agents** view loads.
- In SAP Cloud ALM, **AI Agent Monitoring** is visible.
- In SAP Signavio, the shared Process Intelligence analysis is visible.

![Joule Studio home](images/00_joule-studio-home.png)

![SAP AI Agent Hub home](images/00_leanix-ai-agent-hub-home.png)

> [!CAUTION]
> SAP Cloud ALM and SAP Signavio are read-only in this workshop. Do not change collection, mining, pipeline, or connection settings. Those switches affect the shared tenant.

## Step 3 - Know What Each System Proves

| System | Evidence you will collect |
|---|---|
| SAP Joule Studio | Requirements, tests, evaluations, deployment, and developer trace |
| SAP Cloud Identity Services | User-to-agent assignment and the agent identity boundary |
| SAP AI Agent Hub | Source, ownership, lifecycle, relationships, verification, and MCP dependency |
| SAP Cloud ALM | Cross-agent operational health and a session execution timeline |
| SAP Signavio | Behavior variants, conformance, performance, and improvement evidence |

These are complementary views. A green deployment does not prove that a user is authorized, an agent is governed, or its production behavior is healthy.

## Checkpoint

You have five open system tabs, a participant ID, and a unique custom agent name. If any required system is inaccessible, tell the instructor now and use the paired participant or facilitator fallback path.

## Next

Continue to [Exercise 01 - Map the Architecture](../ex1/README.md).
