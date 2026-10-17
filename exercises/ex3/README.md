# Exercise 03 - Enforce Access and Execute

**Duration:** 15 minutes

In this exercise, you prove that deployment and user access are separate controls. You first observe a denied runtime request, then assign your user to the agent in SAP Cloud Identity Services and repeat the request successfully.

## Objectives

After this exercise, you can:

- Distinguish authentication, user-to-agent access, and backend business authorization.
- Locate the deployed agent identity in SAP Cloud Identity Services.
- Explain least privilege and the intersection of user and agent permissions.
- Compare custom and SAP standard agents under the same identity model.

## Step 1 - Prove the Default Deny

1. Open **Joule Conversations** or the deployed agent's runtime entry point.
2. Select `XP270-NN-Missed-Discount-Agent`.
3. Send the same happy-path request used in Exercise 02.

The invocation should be denied because the deployment has not assigned your user to the agent. Record the visible error category and any correlation or trace ID.

> [!IMPORTANT]
> A denial here is a successful security test. The platform knows the agent exists but refuses the caller before business data is returned. Do not weaken a policy to hide the error.

If the request succeeds immediately, do not remove a shared assignment. Use the instructor-provided restricted agent to observe the same denied state, then continue with your custom agent.

## Step 2 - Locate the Agent Identity

Open the **Agents** administration view in SAP Cloud Identity Services.

1. Search for `XP270-NN-Missed-Discount-Agent`.
2. Open the matching record and verify its name, global tenant or environment, and source/runtime metadata.
3. Confirm that your workshop user is not yet in the agent's user assignment.

An agent identity is not just a display record. It provides an addressable principal for authentication, scoped authorization, policy decisions, and audit correlation.

## Step 3 - Assign Your User

The exact tab label can vary with the workshop tenant version. In the agent record, open the **Users**, **Assignments**, or **Access** section.

1. Choose **Add** or **Assign User**.
2. Search for your exact workshop user, for example `XP268-017`.
3. Select only your user and confirm the assignment.
4. Verify that the user now appears in the assigned list.

> [!CAUTION]
> Do not assign a group, another participant, or an administrator role. This exercise grants invocation access to one agent; it does not grant broader SAP S/4HANA permissions.

## Step 4 - Retry the Custom Agent

Return to the runtime and repeat:

```text
Which five unmatched invoices have the highest early-payment discount at risk?
Show the source fields used for the calculation.
```

Confirm all of the following:

- The agent can now be invoked.
- The response remains read-only and grounded.
- The result contains only data your user is allowed to see.
- A new session or trace was created.

Record the successful session or trace identifier. If the denial remains, sign out and in once to refresh the session, then check that the exact user and agent instance were assigned.

## Step 5 - Compare an SAP Standard Agent

Open the SAP standard finance agent specified by the instructor, such as the **Billing Adjustment Agent**.

1. Inspect its agent card and build type.
2. Send the instructor-provided read-only prompt.
3. If access is denied, check whether the same user-to-agent assignment is missing. Do not change a shared standard-agent assignment without instructor approval.
4. Compare its identity and authorization behavior with your custom agent.

Both custom and standard agents require a governed identity and an authorized caller. Their build source differs; the need for identity-aware enforcement does not.

## How Effective Permission Is Determined

For a user-context invocation, effective access is constrained by both sides:

```text
effective permission = user permission intersection agent permission
```

- The user cannot use the agent to bypass their SAP business roles.
- The agent cannot perform an action outside its own approved scope.
- The target SAP application still makes the final business authorization decision.
- SAP Agent Gateway applies policy checks along the communication path.

## Checkpoint

You have evidence of one denied invocation, one user-to-agent assignment, and one successful invocation. You can explain why granting agent access did not grant invoice-payment authorization.

## Further Study

- [AI Agent Identity and Governance in SAP Landscapes](https://architecture.learning.sap.com/docs/ref-arch/140bdb)
- [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services?locale=en-US)

## Next

Continue to [Exercise 04 - Govern the Agent and MCP Server](../ex4/README.md).
