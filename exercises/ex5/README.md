# Exercise 05 - Diagnose with SAP Cloud ALM

**Duration:** 15 minutes

In this exercise, you use the read-only AI Agent Monitoring application in SAP Cloud ALM to move from portfolio health to one concrete execution bottleneck.

## Objectives

After this exercise, you can:

- Distinguish runtime trace telemetry from evaluation health.
- Navigate from the landing page to an agent, session, and execution step.
- Use flow and timeline views to isolate an error or latency contributor.
- Form a developer handoff that contains enough evidence to act.

## Safety and Data Path

Your workshop role is a viewer. Do not change collection or connection settings.

Agent telemetry is pushed from supported runtimes into SAP Cloud ALM; SAP Cloud ALM does not poll each agent on demand. Two evidence streams may appear:

| Evidence stream | What it tells you |
|---|---|
| Runtime trace | Which components were called, status, sequence, and duration |
| Evaluation result | Whether the agent achieved the task and met quality or compliance criteria |

A trace can be present while health or task-success data is blank if the evaluation service has not supplied results.

## Step 1 - Establish the Time Window

Open **AI Agent Monitoring** and select the instructor-provided period that contains prepared workshop sessions.

On the landing page, inspect:

- total agents and sessions;
- most-used origins or source runtimes;
- session trend and volume;
- common error causes;
- task success or health information, where populated.

Choose one question to carry into the drill-down, for example:

- Did failures increase with volume?
- Is one origin responsible for most errors?
- Is a low success rate caused by one agent or a broader dependency?

## Step 2 - Open the Agent

Choose **Agent List** and search for your custom agent. Newly created telemetry may take time to arrive. If it is absent, open the prepared **Billing Adjustment Agent** or the fallback agent specified by the instructor.

Record:

- session count in the selected period;
- agent health or task success rate, if available;
- error count or error rate;
- the slowest or failed session.

Do not interpret a missing health value as healthy or unhealthy. It means the evidence is unavailable and should be investigated as an instrumentation issue.

## Step 3 - Investigate One Session

Open the selected session. Prefer a session that contains both a meaningful execution flow and an error or long-running step.

1. Open **Execution Flow** and follow the calls from the agent to downstream components.
2. Identify the failed call or the component with the longest duration.
3. Switch to **Timeline**. Expand the hierarchy to see the same execution as a Gantt-style sequence.
4. Compare parent and child durations. A long parent span may simply contain one slow child tool call.
5. Open the detail pane for the problematic step and capture only non-sensitive evidence: component, operation, status, timestamp, duration, and trace/session ID.

The flow view answers "what called what?" The timeline answers "where was time spent?" Use both before assigning a root cause.

## Step 4 - Interpret Evaluation Health

If evaluation health is available, review the contributing metrics. The prepared landscape may include:

- call correctness;
- task success rate;
- output correctness;
- compliance.

These metrics answer a different question from latency. A fast session can still be incorrect; a slow session can still complete successfully.

If evaluation data is absent, add **evaluation telemetry missing** to the operations finding rather than guessing the agent quality.

## Step 5 - Write the Developer Handoff

Complete this concise handoff:

```text
Agent:
Environment and time window:
Session/trace ID:
Observed symptom:
Execution step or dependency:
Status and duration:
Evaluation signal (or missing evidence):
Recommended next check:
```

Good recommendations are specific. Examples include checking an MCP tool timeout, comparing a prompt or agent version, fixing a backend authorization, or restoring evaluation telemetry.

## Checkpoint

You have moved from an aggregated portfolio signal to one session and one likely contributor, without changing the shared tenant. Your handoff separates observed evidence from a hypothesis.

## Troubleshooting

| Symptom | Action |
|---|---|
| New agent is missing | Use the prepared fallback; discovery and telemetry are asynchronous |
| Sessions exist but health is blank | Continue with trace analysis and flag missing evaluation data |
| Session has too little detail | Choose the prepared error session from the instructor's time window |
| Page is slow | Narrow the time range, reload once, and avoid opening multiple session details in parallel |

## Further Study

- [AI Agent Monitoring in SAP Cloud ALM](https://help.sap.com/docs/cloud-alm/applicationhelp/ai-agent-monitoring)
- [SAP AI Agent Hub Reference Architecture](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2)

## Next

Continue to [Exercise 06 - Mine Behavior with SAP Signavio](../ex6/README.md).
