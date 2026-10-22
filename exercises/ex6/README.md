# Exercise 06 - Observe agent behaviour with SAP Signavio (Optional)

> [!NOTE]
> This is an **optional** exercise for those who finish the core path early or want to go deeper on behavioural observability. It stands on its own — you can do it independently of the earlier exercises.

Metrics tell us *whether* an agent is healthy; they don't tell us *how it actually behaves*. Does our finance agent follow the process we expect? Where does it deviate? Which paths are slow or wasteful? Answering that is **process intelligence** applied to agents — and in the SAP landscape that is **SAP Signavio**.

At the end of this exercise, you'll have an understanding of how SAP Signavio mines an agent's execution traces to reveal its real behaviour, and how that complements the monitoring and governance you've already done.

## From traces to behaviour

Every run your agent performs leaves an execution trace — the same raw material you inspected in Joule Studio. **SAP Signavio** ingests these traces and applies **agent mining** to them, giving you three things that pure metrics cannot:

- **Behavioural tracing** — the actual sequence of steps and tool calls each run took, reconstructed into process flows
- **Process conformance** — how closely the agent's real behaviour matches the process it was expected to follow, and where it deviates
- **Performance benchmarking** — comparing paths and runs across the agent landscape to find the slow or costly ones

> [!NOTE]
> This is the same discipline SAP Signavio applies to business processes, now pointed at agents. Instead of mining how a purchase order flows through your systems, you mine how your finance agent flows through its own decisions and tool calls.

## Step 1 — Open SAP Signavio

👉 Open **SAP Signavio** and navigate to the agent mining / process intelligence area for the finance agent.

![Agent mining in SAP Signavio](images/06_signavio-mining.png)

## Step 2 — Explore the mined behaviour

👉 Review the reconstructed process for your agent. Follow the most common path first — the sequence of steps a typical missed-discount-analysis run takes — then look for the variants.

👉 Look at where runs **deviate** from the expected process. A deviation is not necessarily a bug: it might be a legitimate edge case, or it might reveal the agent taking an unexpected route that is worth investigating.

> [!TIP]
> Tie this back to Exercise 2. A widening P99 latency in Joule Studio tells you *some runs are slow*; the mined behaviour here can tell you *which path those slow runs take* — for example, a particular tool call that retries. Metrics find the symptom; behaviour mining helps explain it.

## Step 3 — Think in terms of the landscape

👉 Consider how performance benchmarking works across *many* agents, not just one. Signavio can compare behaviour across the agent landscape, so you can spot which agents are efficient and which are candidates for optimization — or, eventually, for decommissioning.

> [!IMPORTANT]
> **Why this matters:** behaviour mining closes the operate loop. Monitoring (Joule Studio, Cloud ALM) tells you an agent needs attention; governance (AI Agent Hub) controls its lifecycle and approval; and behaviour mining (Signavio) gives you the evidence to decide *what to change* — refine a prompt, fix a tool, or retire the agent.

## Summary

We've seen how SAP Signavio turns raw execution traces into mined behaviour — real process flows, conformance to the expected process, and performance benchmarking across the landscape. Together with Joule Studio monitoring, Cloud ALM operations dashboards, the AI Agent Hub governance record, and the Cloud Identity Services access model, you now have the full picture of operating an agent responsibly at scale: build, monitor, govern, observe, and improve.

That completes the workshop. You have operated an AI agent end to end: understood it, monitored it in Joule Studio, governed it and its MCP server in the AI Agent Hub, managed its identity in Cloud Identity Services, observed it in Cloud ALM, and mined its behaviour with Signavio — the full operations and governance picture for enterprise AI agents on the SAP Business AI Platform.

## Further Study

* [SAP Signavio Process Intelligence](https://help.sap.com/docs/signavio-process-intelligence?locale=en-US)
* [Agentic AI and AI Agents on SAP Business AI Platform (reference architecture)](https://architecture.learning.sap.com/docs/ref-arch/98efa0)

## Next

Return to the 👉 [workshop overview](../../README.md).
