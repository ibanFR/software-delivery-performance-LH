---
title: Measuring Software Delivery Performance
layout: default
parent: Explanation
nav_order: 2
---

# Measuring Software Delivery Performance
{: .no_toc }

Why software delivery is hard to measure, how DORA's research measures it, and how to use the measures to improve
rather than to judge.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Overview

Software Delivery Performance is an outcome a team produces together, not the output of any one person or function.
The research behind [Accelerate] set out to measure it before studying what improves it, and found that how well a team
delivers changes predicts how well the whole organization does.

This page explains the reasoning behind the measures. The five metrics themselves are defined on the
[DORA Metrics][dora-metrics-page] page.

## Why software delivery is hard to measure

> Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is
> invisible. Furthermore, the way we break down work is relatively arbitrary, and the design and delivery
> activities—particularly in the Agile software development paradigm—happen simultaneously.
>
> — *Accelerate*, Ch 2

Lean thinking splits lead time into two parts. Product design and development is a "fuzzy front end": it is unclear
when to start the clock, estimates are uncertain and outcomes vary a lot. Product delivery, from a committed change to
that change running in production, is predictable and has low variability. The research measures the delivery part,
which is why Change Lead Time starts at commit.

## What makes a good measure

*Accelerate* (Ch 2) sets two criteria:

1. **A global outcome, not a local one.** If developers are rewarded for speed and operations for keeping systems up,
   each side protects its own number and the two pull against each other. A good measure is one that different
   functions must collaborate to improve.
2. **Outcomes, not output.** A measure should not reward people for busywork that doesn't help the organization reach
   its goals.

All five DORA metrics are shared by development, operations and release teams for this reason.

## Why not lines of code, velocity or utilization

*Accelerate* (Ch 2) uses three common productivity measures to show what goes wrong when the criteria are ignored:

- **Lines of code.** Rewarding more code leads to bloated software; "we would prefer a 10-line solution to a
  1,000-line solution". Rewarding less code is no better, since it favours clever, unreadable code.
- **Velocity.** Velocity was designed as a capacity planning tool. It is relative to each team, so velocities from
  different teams can't be compared. Used as a productivity measure, "teams inevitably work to game their velocity",
  inflating estimates at the expense of collaboration with other teams.
- **Utilization.** Busy people are not the goal. With no slack, there is no capacity to absorb unplanned work or to
  improve, and "as utilization approaches 100%, lead times approach infinity".

Martin Fowler reaches the same conclusion in [Cannot Measure Productivity]: "false measures only make things worse".

## From four measures to five

*Accelerate* reported four measures: delivery lead time and deployment frequency for tempo, time to restore service and
change fail rate for stability. DORA has refined them since, as told in [A history of DORA's software delivery
metrics]:

| Year | Change                                                                                                                   |
|------|--------------------------------------------------------------------------------------------------------------------------|
| 2014 | Four measures. Change fail rate did not correlate with the others, so the statistical construct used only three.         |
| 2015 | The measures settle into two groups: throughput (deployment frequency, lead time) and stability (MTTR, change fail rate). |
| 2023 | MTTR becomes Failed Deployment Recovery Time, counting only failures caused by a change, not outages from outside.       |
| 2024 | Deployment Rework Rate is added, and the five metrics are regrouped into Throughput and Instability.                     |

Older sources use other names for the same ideas. When reading *Accelerate* or past State of DevOps reports:

| Older term                                      | Term used on this site                                         |
|-------------------------------------------------|----------------------------------------------------------------|
| delivery lead time, lead time for changes       | Change Lead Time                                               |
| time to restore service, MTTR                   | Failed Deployment Recovery Time (narrower, now in Throughput)  |
| change failure rate                             | Change Fail Rate                                               |
| tempo                                           | Throughput                                                     |
| stability                                       | Instability (now Change Fail Rate and Deployment Rework Rate)  |
| IT performance, SDO performance                 | Software Delivery Performance                                  |

Older material groups recovery time with stability. DORA now places Failed Deployment Recovery Time in Throughput, and
this site follows the current grouping.

## Throughput and Instability move together

The most cited finding of the research is that there is no trade-off between moving fast and keeping deployments
safe:

> there is no tradeoff between improving performance and achieving higher levels of stability and quality. Rather,
> high performers do better at *all* of these measures.
>
> — *Accelerate*, Ch 2

In the 2017 data, high performers compared with low performers had 46 times more frequent deployments, 440 times
faster lead time from commit to deploy, 170 times faster recovery and a 5 times lower change failure rate (*Accelerate*,
Ch 1). DORA still states it today: "speed and stability are not tradeoffs" ([DORA's software delivery performance
metrics]).

The finding describes the population and its best performers, not every team. Some groups show other shapes:

- In 2022, a cluster of teams deployed rarely but succeeded when they did ([2022 report announcement]).
- In 2025, DORA described a team profile with low performance, high system stability and high burnout, and found that AI
  adoption raised Throughput while hurting stability ([2025 report announcement]).

This is why both groups have to be read together, for your own application or service.

## How DORA measures

### Surveys, not system data

DORA's research is based on surveys of thousands of practitioners each year, asked about "the primary application or
service you work on". The questions offer the same six answer bands, from "less than one hour" to "more than six
months", that appear in *Accelerate*, which makes results comparable from year to year.

*Accelerate* (Ch 14) gives the reasons for surveys:

- They collect data quickly, across many organizations, with the same words and definitions for everyone. Teams that
  measure their own pipelines often mean different things by "lead time".
- System data only sees what the tools see. It misses work outside the toolchain and the experience of the people
  doing the work.
- Survey data can be trusted at scale. Responses are anonymous, and with tens of thousands of respondents it would take
  hundreds of people lying in a coordinated way to shift the results.

Survey and system data are complementary: "all measures are proxies" (*Accelerate*, Ch 13), and a team improving its
own delivery will often use data from its pipeline.

### Constructs and clusters

Software Delivery Performance can't be observed directly, so the research treats it as a *latent construct*: something
measured through several survey items, each checked for validity and reliability before any analysis.

Performance groups come from *cluster analysis*, which groups similar responses together. The technique "doesn't know
what counts as a 'good' or 'bad' response" (*Accelerate*, Ch 2), yet every year it found high, medium and low
performers that differ on all the measures.

The research then goes beyond correlation, using statistical methods that test whether one thing *predicts* another.
That is still not the same as proof of cause from an experiment.

### Limitations

The authors list the limits of their own method (*Accelerate*, Ch 15):

- Each survey is a snapshot at a single point in time.
- Respondents are reached through mailing lists and social media, not a random sample, and are mostly people who
  already know about DevOps.
- People may paint their team in a favourable light. The questions ask about concrete practices, never "do you practice
  continuous integration?", to reduce this.

Clusters are also recomputed from each year's respondents, so the thresholds for "high" or "elite" move every year.
A benchmark table is a snapshot of that year's survey, not a fixed standard.

## Why it matters

Software Delivery Performance predicts organizational performance. In *Accelerate* (Ch 2), high performers were twice
as likely as low performers to exceed their goals for profitability, market share and productivity. The same held for
noncommercial goals such as customer satisfaction, quality and achieving the organization's mission.

DORA describes the metrics as leading indicators of organizational performance and well-being, and lagging indicators
of practices ([DORA's software delivery performance metrics]). Teams improve the metrics by improving their
capabilities, such as continuous integration or loosely coupled architecture. *Accelerate* (Ch 1) argues for
capability models over maturity models, because there is no level at which a team has "arrived": what counts as
high-performing keeps rising.

## Measuring your own team

DORA's pitfalls are listed on the [DORA Metrics][dora-metrics-page] page. The research adds the reasons behind them:

- **Measure one application or service at a time**, and compare it with its own past rather than with other teams.
  DORA has always asked about a primary application or service, and "comparing your metrics year-over-year is more
  meaningful than comparing yourself to other companies" ([2023 report announcement]).
- **Don't turn the metrics into targets.** When a measure becomes a target, it ceases to be a good measure (Goodhart's
  law). *Accelerate* shows the same with velocity, and DORA lists "setting metrics as a goal" as its first pitfall.
- **Start with a conversation, not a dashboard.** The [DORA Quick Check] in a retrospective gives a team a baseline in
  minutes. Thoughtworks recommends using the metrics "for team reflection and learning rather than just building
  complex dashboards" ([Thoughtworks Technology Radar]).
- **Include what users experience.** Metrics computed only from a pipeline miss incidents that degrade service for
  users, which is what Change Fail Rate and Failed Deployment Recovery Time are about.
- **Measure in a culture without fear.** In pathological and bureaucratic cultures, "measurement is used as a form of
  control, and people hide information". As Deming said, "whenever there is fear, you get the wrong numbers"
  (*Accelerate*, Ch 2).

## Open questions

The research is still evolving, and DORA says so itself:

- **Change Fail Rate behaves differently.** It did not correlate with the other measures in 2014, and in 2016 medium
  performers did worse on it than low performers (*Accelerate*, Ch 2). The 2024 regrouping into a separate Instability
  group reflects this.
- **The clusters change from year to year.** An "elite" cluster appeared in 2018, was missing in 2022 and returned in
  2023. DORA offers both a real shift during the pandemic and an artefact of sampling a different set of respondents
  each year as explanations ([2022 report announcement], [DORA FAQ]).

## Further Reading

- [Accelerate], especially Ch 2 "Measuring Performance" and Part II on the research method
- [DORA's software delivery performance metrics]
- [A history of DORA's software delivery metrics]
- [DORA Quick Check]
- [DORA research]
- [The SPACE of Developer Productivity]

Metric history and guidance quoted from [DORA]. Book quotations from *Accelerate: The Science of Lean Software and
DevOps* by Nicole Forsgren, Jez Humble and Gene Kim (IT Revolution, 2018).

[dora-metrics-page]: {% link explanation/dora-metrics.md %}
[Accelerate]: https://itrevolution.com/product/accelerate/
[DORA]: https://dora.dev/
[DORA's software delivery performance metrics]: https://dora.dev/guides/dora-metrics/
[A history of DORA's software delivery metrics]: https://dora.dev/guides/dora-metrics/history/
[DORA Quick Check]: https://dora.dev/quickcheck/
[DORA research]: https://dora.dev/research/
[DORA FAQ]: https://dora.dev/faq/
[2022 report announcement]: https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/
[2023 report announcement]: https://cloud.google.com/blog/products/devops-sre/announcing-the-2023-state-of-devops-report
[2025 report announcement]: https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report
[Cannot Measure Productivity]: https://martinfowler.com/bliki/CannotMeasureProductivity.html
[Thoughtworks Technology Radar]: https://www.thoughtworks.com/en-gb/radar/techniques/dora-metrics
[The SPACE of Developer Productivity]: https://queue.acm.org/detail.cfm?id=3454124
