# Exercise 05 - Observe your agent in SAP Cloud ALM

In Exercise 2 we watched our agent's health from the *build* side, in Joule Studio. In Exercise 3 we governed it and in Exercise 4 we established its identity and access. Now we look at the dedicated **operations** view. In an enterprise, day-to-day production health is typically watched by an operations team — and the tool they use for that across SAP solutions is **SAP Cloud ALM**.

At the end of this exercise, you'll have an understanding of how agent telemetry reaches SAP Cloud ALM and what the operations team watches there.

> [!IMPORTANT]
> This exercise is a **guided, read-only walkthrough**. Your trainer will demonstrate SAP Cloud ALM live — you do not need to log in. Follow along with the screenshots and focus on *what* is being shown and *why* it matters, rather than clicking yourself.

## How telemetry gets to Cloud ALM

Session telemetry from SAP-managed agents flows automatically into **SAP Cloud ALM**, where it drives performance dashboards. This is the same execution data you saw summarized in Joule Studio — but presented for operations: aggregated across agents, trended over time, and designed for someone watching the whole landscape rather than debugging a single solution.

> [!NOTE]
> Recall the Connected systems on the AI Agent Hub dashboard from Exercise 3 — **SAP Cloud ALM** was one of them. The AI Agent Hub also surfaces this observability so governance and operations share a consistent view.

## Step 1 — Watch the agent observability dashboard

👉 Follow along as your trainer opens the agent observability dashboards in **SAP Cloud ALM**.

![Agent performance dashboard in SAP Cloud ALM](images/04_calm-dashboard.png)

As the dashboard is shown, note the kinds of signal operations rely on:

- **Evaluation rates** — how well the agent's responses are scoring over time
- **Error patterns** — where and how runs are failing, and whether failures cluster
- **Session volumes** — how much the agent is actually being used
- **Trends** — how all of the above move day over day

## Step 2 — Connect it back to what you've seen

👉 As you watch, map each Cloud ALM signal to its Joule Studio counterpart from Exercise 2 — error patterns to the Trace Error Rate chart, session volumes to Trace Count, and so on.

> [!TIP]
> The distinction is about audience, not data. **Joule Studio** monitoring is where a *developer* validates a change or investigates a specific trace. **Cloud ALM** is where *operations* watches production health across many agents and decides when to escalate. When operations finds a failing run they cannot resolve, they hand the **trace ID** back to the developer — closing the loop you saw in Exercise 2.

## Summary

We've seen how agent telemetry flows into SAP Cloud ALM and what an operations team watches there — evaluation rates, error patterns, session volumes, and trends — and how that complements the developer-facing monitoring in Joule Studio. In the next exercise we look at agent *behaviour* with SAP Signavio.

## Further Study

* [SAP Cloud ALM](https://help.sap.com/docs/cloud-alm?locale=en-US)
* [AI Agent Hub (reference architecture)](https://architecture.learning.sap.com/docs/ref-arch/jkg4j2)

## Next

Continue to 👉 [(Optional) Exercise 06 - Observe agent behaviour with SAP Signavio](../ex6/README.md)
