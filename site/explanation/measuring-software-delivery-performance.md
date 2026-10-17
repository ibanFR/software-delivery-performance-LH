---
title: Measuring Software Delivery Performance
layout: default
parent: Explanation
nav_order: 2
---

# Measuring Software Delivery Performance
{: .no_toc }

Why software delivery is hard to measure, what DORA's research found, and how to interpret its measures. The headline finding, that Throughput and Instability do not trade off, is a DORA program finding. No replication outside DORA has been found.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Overview

This page is background reading for Participants in this Learning Hour. It explains why the measures are built the way they are. The five metrics are covered on the [DORA Metrics][dora-metrics-page] page. This page quotes DORA's own wording in "The DORA framework today".

Software Delivery Performance is how well a team delivers changes to an application or service. DORA measures it with five metrics taken together. The research behind those metrics is the *Accelerate* research, which began in 2014.

Keep one caveat in mind. The headline finding, that Throughput and Instability do not trade off, comes from DORA's own program. Martin Fowler's foreword to *Accelerate* endorses it, but Fowler does not test the claim. The foreword is printed in the program's own book.

## Why software delivery is hard to measure

> Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is invisible.
>
> *Accelerate*, Ch 2

Design and delivery also overlap. The book splits the path to production into two parts. The design part is a "fuzzy front end", where "it's often unclear when to start the clock." The delivery part is easier to measure. It runs from a committed change to a change running in production, and it "has a lower variability" (*Accelerate*, Ch 2). The research measures the delivery part. That is why Change Lead Time starts at the commit.

## What makes a good measure

*Accelerate* (Ch 2) sets two criteria for a good measure.

1. **A global outcome, not a local one.** Teams should not be pitted against each other. The book's example is developers rewarded for "throughput" and operations rewarded for "stability." Each side then protects its own number. The book calls the result a "wall of confusion."
2. **Outcomes, not output.** A measure should not reward busywork. The book says it "shouldn't reward people for putting in large amounts of busywork."

DORA's guidance asks development, operations and release teams to share all five metrics. It lists siloed ownership as a pitfall.

## Why not lines of code, velocity or utilization

*Accelerate* (Ch 2) uses three common output measures to show what goes wrong.

- **Lines of code.** The book would "prefer a 10-line solution to a 1,000-line solution to a problem."
- **Velocity** (a historical term, not used for Software Delivery Performance). It is "a relative and team-dependent measure, not an absolute one," and teams "inevitably work to game their velocity" when it is used as output.
- **Utilization.** "As utilization approaches 100%, lead times approach infinity," a point the book supports with queueing theory.

Martin Fowler reaches a similar conclusion in [Cannot Measure Productivity] (2003). He writes that "false measures only make things worse."

## From four measures to five

*Accelerate* reported four measures. DORA has refined them since ([A history of DORA's software delivery metrics]).

| Year | Change |
|---|---|
| 2014 | Four measures. Change fail rate did not correlate with the others, so the statistical construct used three. |
| 2015 | Two groups: throughput (deployment frequency and lead time) and stability (time to restore and change fail rate). These are historical group names. |
| 2023 | Mean time to restore (MTTR, historical) became Failed Deployment Recovery Time. |
| 2024 | Deployment Rework Rate was added. Failed Deployment Recovery Time moved into Throughput. The groups became Throughput and Instability. |
| 2025 | Performance tiers gave way to seven team profiles. DORA calls their names "an interpretation of the data" (2025 report, p. 16). |

Older material uses other names. Lead time for changes, time to restore service, MTTR and change failure rate are older names for Change Lead Time, Failed Deployment Recovery Time and Change Fail Rate. Older material put recovery time in the Stability group. DORA now places Failed Deployment Recovery Time in Throughput, and this site follows that grouping.

## The DORA framework today

DORA groups its five metrics into two groups. The definitions below are quoted from DORA's own guide ([DORA's software delivery performance metrics], updated 2026).

**Throughput** is "a measure of how many changes can move through the system over a period of time." Its metrics are:

- **Change Lead Time**: "The amount of time it takes for a change to go from committed to version control to deployed in production."
- **Deployment Frequency**: "The number of deployments over a given period or the time between deployments."
- **Failed Deployment Recovery Time**: "The time it takes to recover from a deployment that fails and requires immediate intervention."

**Instability** is "a measure of how well the software deployments go." Its metrics are:

- **Change Fail Rate**: "The ratio of deployments that require immediate intervention following a deployment. Likely resulting in a rollback of the changes or a "hotfix" to quickly remediate any issues."
- **Deployment Rework Rate**: "The ratio of deployments that are unplanned but happen as a result of an incident in production."

The 2024 report describes the throughput factor as measuring "the speed of making updates of any kind, normal changes and changes in response to a failure" (DORA 2024 report, p. 12). That is a description, not a statistical test. The report calls the second group "software delivery stability." DORA's guide and the 2025 report use Instability, and this page does too.

## Throughput and Instability move together

The best-known finding is that Throughput and Instability do not trade off. The book says so directly:

> there is no tradeoff between improving performance and achieving higher levels of stability and quality. Rather, high performers do better at *all* of these measures.
>
> *Accelerate*, Ch 2, 2014-2017 data

In the 2017 data, high performers had 46 times more frequent deployments and a 5 times lower change failure rate than low performers (*Accelerate*, Ch 1). The book uses historical metric names. DORA's current guide makes the same claim: "DORA's research has repeatedly demonstrated that speed and stability are not tradeoffs."

**Status of the claim.** This is a DORA program finding. Fowler's foreword endorses it: "speed depends on stability, so good IT practices give you both." Thoughtworks lists the metrics on its [Thoughtworks Technology Radar], but neither source tests the trade-off claim. No replication outside DORA has been found.

**Correlation, not cause.** The finding describes patterns across survey respondents. It shows that the two groups are not opposed across the population. It does not show that raising Throughput makes Instability fall.

**Proposed mechanisms.** The authors propose two mechanisms. Their evidence is inferential and comes from DORA's own data.

- **Small batches.** The book uses Deployment Frequency as "a proxy for batch size."
- **Fast feedback and continuous delivery.** The book argues that continuous delivery "predicts lower change fail rates" (Ch 4).

**Dated exceptions.** The pattern has not held in every year or for every group.

- **2014.** Change fail rate "did not significantly correlate with the other variables" (DORA's metric history, 2026). It stayed out of the 2014-2017 construct.
- **2016-2017.** In 2016, medium performers did worse than low performers on change fail rate. The book says "Our research doesn't conclusively explain this" (Ch 2). In 2017, low performers "lose some ground in stability." The book suspects attempts to increase tempo (Ch 2).
- **2022-2023.** No Elite cluster appeared in 2022. Low performers rose from 7% in 2021 to 19% in 2022, and the Medium cluster held 69% of respondents ([2022 report announcement]). DORA offered the pandemic as one hypothesis. Its FAQ allows that differences "may be artifacts of sampling and analysis methods" ([DORA FAQ]). Elite performers returned in 2023, and were "able to achieve both throughput and stability" ([2023 report announcement]).
- **2024, Medium and High.** The 2024 report found four clusters: Elite 19%, High 22%, Medium 35% and Low 25% (DORA 2024 report, p. 13). The Medium cluster had a Change Fail Rate of 10%, below the High cluster's 20% (p. 13). DORA explains that "This correlation persists even in the medium performance cluster" (p. 14). It also explains its labels: "We made a decision to call the faster teams 'high performers,' and the slower but more stable teams 'medium performers'" (p. 14). Within each cluster, the report says, Throughput and Instability are correlated (p. 14). Even so, more than half of the teams showed differences between the two (p. 11).
- **2024, AI.** Each 25% increase in AI adoption came with "an estimated 1.5% reduction" in throughput and "an estimated 7.2% reduction" in stability (p. 40). The report links this to a field that may have forgotten "the importance of small batch sizes," and points to changelists growing in size (p. 40).
- **2025, AI.** "AI adoption now improves software delivery throughput, a key shift from last year. However, it still increases delivery instability" (DORA 2025 report, p. 4). The 2025 report restates the 2024 AI result using Instability (p. 35).

**Reading the exceptions.** The no-trade-off pattern holds across the population and for top performers. Middle clusters, particular teams and some interventions, such as AI adoption, can show the two groups moving apart. The 2024 report says "emerging evidence suggests these factors operate with sufficient independence to warrant separate consideration" (DORA 2024 report, p. 39). This fits DORA's decision to report them as separate factors since 2024.

## How DORA measures

**Surveys.** DORA asks practitioners about "the primary application or service you work on" ([DORA 2024 survey questions]). The book gives two reasons for using surveys (Ch 14):

- Every respondent gets the same items, words and definitions.
- Responses are anonymous. It would take several hundred people lying in a coordinated way to change the results noticeably.

The book argues that survey data can be trusted at scale. That is the program's own argument, not an outside check. The book also says that "all measures are proxies" (Ch 13).

**Constructs.** The book treats Software Delivery Performance as a "latent construct," measured through several survey items. Each item is checked for validity and reliability before analysis (Ch 13).

**Clusters.** Cluster analysis groups similar respondents. It "categorizes the data without any bias toward 'good' or 'bad'" (Ch 2). In 2014-2017 the groups "were all significantly different across all four measures" (Ch 2).

**From correlation toward prediction.** They used prediction tests. They state that they did no causal analysis. The book says causal analysis "generally requires randomized studies" (Ch 12).

**Limits.** The authors list the limits of their own method (*Accelerate*, Ch 15):

- Each survey is a single snapshot, which "precluded us from longitudinal analysis."
- Respondents came from mailing lists and social media, not a random sample. Puppet's lists were among them. The authors add, "We miss a cohort that are likely performing even worse than our low performers."
- Respondents "might want to paint their team or organization in a favorable light." The questions ask about practices, not labels, to reduce this.

DORA's FAQ adds that DORA does "not share the raw data" ([DORA FAQ]). Puppet, a DevOps tooling company, ran the work in 2014-2017. DORA joined Google Cloud in 2018 ([DORA joined Google Cloud]), and it is a program run by Google Cloud today.

Martin Fowler's foreword raises further doubts. Surveys "capture subjective perceptions," and he questions how well the sample reflects IT in general. He also notes that the book covers "the journey from commit to production, not the entire software development process."

An outside view is limited. A 2023 preprint by Sánchez Ruiz and colleagues argues that the DORA benchmark cannot be applied to open source projects without adaptation ([Sánchez Ruiz et al., arXiv 2023]). Those projects release code continuously rather than deploying to production.

## Why it matters

In the 2014-2017 data, high performers were twice as likely as low performers to exceed their goals. The goals were for profitability, market share and productivity (*Accelerate*, Ch 2). For noncommercial goals in 2017, the book reports the same pattern (Ch 2). This is a pattern across survey respondents. The research does not show that improving the metrics will by itself raise profit.

DORA describes the metrics as "leading indicators" of organizational performance and well-being. It calls them "lagging indicators" of delivery practices ([DORA's software delivery performance metrics]). The book identifies 24 key capabilities from its 2014-2017 data (Ch 1), which it says "drive improvement in software delivery performance." The book argues against maturity models, and says they end up being vanity metrics (Ch 1). These links are the authors' model.

## Common pitfalls

DORA lists seven pitfalls on the [DORA Metrics][dora-metrics-page] page. This section gives the reasons and the evidence for the main ones.

**A conflict to know about.** The book and DORA's current guidance disagree on targets and benchmarks. In Ch 2 the authors write "ask your teams to set targets for these measures." They also say teams can be compared and benchmarked against the larger organizations they work in. DORA's current guidance lists setting metrics as a goal, and making disparate comparisons, among its pitfalls. This page follows the current guidance. The book's own warning applies: in pathological cultures, "measurement is used as a form of control."

**Setting targets.** When a measure becomes a target, people game it. This is Goodhart's law. Academic work describes several routes to this ([Manheim and Garrabrant, arXiv 2018]). That work covers proxy measures in general, not DORA metrics. The product page for Bryan Finster's 2022 guidance paper, from IT Revolution, says the metrics are often misapplied as standalone improvement targets ([IT Revolution product page]).

**One metric or one group.** DORA warns against having one metric to rule them all. The 2025 DORA announcement says: "Simple software delivery metrics alone aren't sufficient. They tell you what is happening but not why it's happening" ([2025 report announcement]).

**Comparing teams.** DORA says the metrics work best for "one application or service at a time." The 2024 report says "Improving should be more important to a team than reaching a particular performance level" (p. 14). DORA's guidance is to compare a team with its own past. Benchmarks are yearly snapshots, since respondents differ each year ([DORA FAQ]).

**Industry as a shield.** Regulation or domain rules do not rule out improvement. The 2024 report says industry rarely predicts performance, and high-performing teams appear "in every industry vertical" (p. 15).

**Individuals.** Activity metrics "should never be used in isolation either to reward or to penalize developers," Forsgren is reported as saying in 2021 ([InfoQ SPACE article]).

**Measurement before improvement.** Thoughtworks warns against spending "weeks to build up sophisticated dashboard tooling" (2021). A practitioner reported in 2021 that measuring was "more time-consuming than I thought" ([InfoQ Huber report]).

**Fear.** As Deming put it, "whenever there is fear, you get the wrong numbers" (Ch 2).

## What remains open

- **Replication.** The no-trade-off claim has not been replicated outside DORA.
- **Change Fail Rate.** Its place in the framework has moved, in 2014, 2016 and the 2024 regrouping.
- **Recovery time.** DORA describes its place in Throughput (2024 report, p. 12). That is a description, not a statistical test.
- **Yearly clusters.** Cluster thresholds change from year to year, so each year's benchmark is a snapshot.

## Further reading

- *Accelerate*, especially Ch 2 and Part II on the research method ([Accelerate]).
- [DORA's software delivery performance metrics] and [A history of DORA's software delivery metrics].
- [DORA Quick Check], for a baseline in a retrospective.
- [DORA research], for the annual reports.
- [SPACE of Developer Productivity]. SPACE is co-authored by Forsgren, so it is a related framework, not an outside check.
- [Facilitation Guide], for how the Learning Hour uses these measures.

Metric definitions and history are quoted from DORA. Book quotations are from *Accelerate: The Science of Lean Software and DevOps* by Nicole Forsgren, Jez Humble and Gene Kim (IT Revolution, 2018), with a foreword by Martin Fowler. Reports cited: [DORA 2024 report] and [DORA 2025 report].

[dora-metrics-page]: {% link explanation/dora-metrics.md %}
[Facilitation Guide]: {% link how-to/facilitation-guide.md %}
[Accelerate]: https://itrevolution.com/product/accelerate/
[Cannot Measure Productivity]: https://martinfowler.com/bliki/CannotMeasureProductivity.html
[A history of DORA's software delivery metrics]: https://dora.dev/guides/dora-metrics/history/
[DORA's software delivery performance metrics]: https://dora.dev/guides/dora-metrics/
[DORA 2024 report]: https://dora.dev/research/2024/
[DORA 2025 report]: https://dora.dev/research/2025/
[DORA 2024 survey questions]: https://dora.dev/research/2024/questions/
[DORA FAQ]: https://dora.dev/faq/
[DORA joined Google Cloud]: https://dora.dev/news/dora-joins-google-cloud/
[DORA Quick Check]: https://dora.dev/quickcheck/
[DORA research]: https://dora.dev/research/
[2022 report announcement]: https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/
[2023 report announcement]: https://cloud.google.com/blog/products/devops-sre/announcing-the-2023-state-of-devops-report
[2025 report announcement]: https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report
[Thoughtworks Technology Radar]: https://www.thoughtworks.com/en-gb/radar/techniques/dora-metrics
[IT Revolution product page]: https://itrevolution.com/product/how-to-misuse-abuse-dora-metrics/
[Manheim and Garrabrant, arXiv 2018]: https://arxiv.org/abs/1803.04585
[Sánchez Ruiz et al., arXiv 2023]: https://arxiv.org/abs/2304.14790
[InfoQ SPACE article]: https://www.infoq.com/news/2021/03/space-developer-productivity
[InfoQ Huber report]: https://www.infoq.com/news/2021/08/measuring-four-key-metrics/
[SPACE of Developer Productivity]: https://queue.acm.org/detail.cfm?id=3454124
