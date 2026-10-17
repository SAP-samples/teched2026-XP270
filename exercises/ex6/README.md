# Exercise 06 - Mine Behavior with SAP Signavio

**Duration:** 10 minutes

In this exercise, you use SAP Signavio Process Intelligence to look beyond one trace. You compare execution paths, identify a deviation or bottleneck, and connect agent behavior to a business improvement decision.

## Objectives

After this exercise, you can:

- Explain how OpenTelemetry traces become an event log for process analysis.
- Distinguish session diagnosis from cross-session behavior mining.
- Use variants, performance, errors, and conformance as complementary evidence.
- Identify privacy and tenant-isolation considerations for agent traces.

## From Trace to Event Log

For supported agents, execution traces are normalized by the AI Agent Mining connector into events that SAP Signavio Process Intelligence can analyze.

| Trace concept | Process Intelligence concept |
|---|---|
| Agent session or execution | Case |
| Reasoning/tool step | Event or activity |
| Start and end time | Timestamp and duration |
| Agent, model, tool, status | Event attributes |

This transformation enables comparison across many executions. SAP Cloud ALM helped you diagnose one session; SAP Signavio helps you ask whether that path is common, exceptional, non-conforming, or expensive.

## Step 1 - Open the Agent Mining Analysis

Open the shared SAP Signavio workspace and navigate to **Process Intelligence**. Open the analysis supplied by the instructor for AI Agent Mining.

Apply the workshop filters:

- agent type or name: the prepared finance or Billing Adjustment agent;
- tenant/environment: the workshop tenant;
- time range: the period supplied by the instructor.

If SAP AI Agent Hub exposes a direct mining link on the agent instance, compare its filters with the analysis you opened manually.

## Step 2 - Read the Performance Overview

Open **Analyze Agent Execution Performance** or the prepared overview page. Inspect the available measures, such as:

- total executions and successful or failed executions;
- average or percentile duration;
- tool or LLM cost, where available;
- activity or tool-call frequency;
- error and retry patterns.

Choose one signal that matches the Cloud ALM finding. For example, if Cloud ALM showed a slow invoice tool call, look for high duration or repeated calls to that activity across cases.

## Step 3 - Compare Variants

Open the process or variant explorer.

1. Select the most frequent successful path as the baseline.
2. Select a slower or failed variant.
3. Compare activity order, retries, loops, skipped steps, and duration.
4. Decide whether the variant is an expected business exception or an unintended deviation.

Use this reasoning pattern:

```text
Observed variant -> likely technical or business cause -> business impact -> action
```

Example:

```text
Repeated invoice lookup -> retry after backend timeout -> slower discount review
and risk of missing the payment window -> inspect timeout and retry policy.
```

## Step 4 - Check Conformance and Value

Where a reference model or conformance view is available, identify an execution that does not follow the expected read-only path.

Ask:

- Did the agent call only approved tools?
- Did it skip a validation or human checkpoint?
- Did a retry improve success or only add cost and latency?
- Did the agent reduce the business cycle time or only shift the bottleneck?

Agent mining should ultimately connect behavior to business outcomes. A technically successful agent is not valuable if invoice handling becomes slower, exceptions rise, or discount savings do not improve.

## Data Privacy Check

Agent traces can contain prompts, identifiers, tool arguments, and business data. Before broadening access to an analysis, architects must check anonymization or pseudonymization, retention, data residency, and tenant isolation. Do not expose raw payloads in screenshots or workshop notes.

> [!NOTE]
> The Architecture Center's agent behavior mining page describes capabilities for next-generation SAP agents and marks parts of the model as forward-looking. Treat the live training tenant and current SAP Help as the source of truth for available fields and supported agent types.

## Checkpoint

You identified a common path, a meaningful variant, and one evidence-based improvement action. You can explain why this conclusion required cross-session behavior data rather than a single trace alone.

## Further Study

- [Analyze Agent Execution Performance](https://help.sap.com/docs/signavio-process-intelligence/reference-guide-for-value-accelerators/analyze-agent-execution-performance?c=742fb724)
- [AI Agent Behavior Mining with SAP Signavio](https://architecture.learning.sap.com/docs/ref-arch/3c8d50)
- [SAP Signavio Process Intelligence](https://help.sap.com/docs/signavio-process-intelligence?locale=en-US)

## Next

Continue to [Exercise 07 - Close the Control Loop](../ex7/README.md).
