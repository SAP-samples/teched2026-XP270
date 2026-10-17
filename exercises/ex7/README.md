# Exercise 07 - Close the Control Loop

**Duration:** 5 minutes

In this final exercise, you turn the evidence collected across six products into one architecture decision.

## Step 1 - Complete the Evidence Chain

Use your workshop findings to complete the table:

| Lifecycle question | Evidence source | Your conclusion |
|---|---|---|
| Was the intended behavior specified and tested? | SAP Joule Studio requirements and evaluations | |
| Was access denied by default and assigned deliberately? | SAP Cloud Identity Services and runtime denial | |
| Is ownership and business context explicit? | SAP AI Agent Hub fact sheet | |
| Is the tool boundary governed? | MCP server relationship and assessment | |
| Is the runtime healthy? | SAP Cloud ALM session and evaluation evidence | |
| Does behavior conform across executions? | SAP Signavio variants and conformance | |

## Step 2 - Make the Decision

Choose one decision and state its evidence:

- **Activate or continue:** controls pass and no material operational issue remains.
- **Remediate:** the use case remains valid, but a specific control, dependency, or behavior must change.
- **Restrict:** reduce users, tool scope, or environment while evidence is incomplete.
- **Phase out:** business value does not justify the operational, risk, or duplication cost.

Use this architecture decision record:

```text
Decision:
Evidence:
Known risk or missing evidence:
Owner:
Action and due date:
Success measure:
```

## End-to-End Result

You have completed an enterprise agent control loop:

```text
Design -> Test -> Deploy -> Deny -> Authorize -> Execute
       -> Discover -> Govern -> Monitor -> Mine -> Improve
```

The most important lesson is that no single dashboard proves an agent is enterprise-ready. Trust comes from connected evidence across build quality, identity, authorization, ownership, dependencies, runtime health, and business behavior.

## Further Study

- [Agentic AI & AI Agents on SAP Business AI Platform](https://architecture.learning.sap.com/docs/ref-arch/98efa0)
- [SAP AI Agent Hub for Enterprise AI Governance](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2)
- [SAP's Global Standards for Agentic AI](https://architecture.learning.sap.com/docs/global-standards-for-agentic-ai)

Return to the [workshop overview](../../README.md).
