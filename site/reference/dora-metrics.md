---
title: DORA Metrics
layout: default
parent: Reference
nav_order: 1
---

# DORA Metrics
{: .no_toc }

The five metrics that make up Software Delivery Performance, with each definition, unit and survey question.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Scope

DORA says the metrics are best suited to measuring one application or service at a time ([DORA's software delivery performance metrics][]).

Each metric below uses the same fields, in the same order. Definitions are quoted from DORA. Other facts cite the year and page of the source. For why DORA chose these metrics, see [Measuring Software Delivery Performance][].

## Summary

| Metric | Group | Definition in short | Unit |
|:-------|:------|:--------------------|:-----|
| Change Lead Time | Throughput | Time from a change committed to version control until it is deployed in production | Duration |
| Deployment Frequency | Throughput | Number of deployments over a period, or time between deployments | Count per period, or interval |
| Failed Deployment Recovery Time | Throughput | Time to recover from a deployment that fails and requires immediate intervention | Duration |
| Change Fail Rate | Instability | Ratio of deployments that require immediate intervention after a deployment | Percentage |
| Deployment Rework Rate | Instability | Ratio of deployments that are unplanned and happen because of a production incident | Percentage |

The "Definition in short" column is a paraphrase. The full definition for each metric is in its section.

## Throughput

> "Throughput is a measure of how many changes can move through the system over a period of time."
>
> DORA, [DORA's software delivery performance metrics][]

Throughput contains three metrics: Change Lead Time, Deployment Frequency and Failed Deployment Recovery Time.

### Change Lead Time

> "The amount of time it takes for a change to go from committed to version control to deployed in production."
>
> DORA, [DORA's software delivery performance metrics][]

- **Group:** Throughput.
- **Measures:** Starts when a change is committed to version control. Ends when the change is deployed in production. "Change" covers changes of any kind, including changes to configuration and changes to code ([DORA 2024 report][], p. 10).
- **Unit:** Duration. DORA does not specify whether to aggregate with a median or a mean.
- **Survey question (2024):** "What is your lead time for changes (i.e., how long does it take to go from code committed to code successfully running in production)?" Answers are six time bands, from "Less than one hour" to "More than six months", plus "I don't know or NA". The 2025 survey asks the same question, with "that is" in place of "i.e." ([DORA 2024 questions][]; [DORA 2025 questions][]).
- **Former names:** "deployment lead time" (2015 model); "delivery lead time" ([Accelerate][], 2018). The survey used "lead time for changes" from 2022 to 2025.

### Deployment Frequency

> "The number of deployments over a given period or the time between deployments."
>
> DORA, [DORA's software delivery performance metrics][]

- **Group:** Throughput.
- **Measures:** Deployments to production. In [Accelerate][] (2018), a deployment is a software deployment to production or to an app store. DORA does not say how to count deployments in an automated system.
- **Unit:** Count per period, or interval between deployments. The survey records a frequency band.
- **Survey question (2024):** "How often does your organization deploy code to production or release it to end users?" Answers are six frequency bands, from "Fewer than once per six months" to "On demand (multiple deploys per day)", plus "I don't know or NA". The 2025 survey asks the same question with the same answers ([DORA 2024 questions][]; [DORA 2025 questions][]).
- **Former names:** "release frequency" ([Accelerate][], 2018, chapter 3).

### Failed Deployment Recovery Time

> "The time it takes to recover from a deployment that fails and requires immediate intervention."
>
> DORA, [DORA's software delivery performance metrics][]

- **Group:** Throughput, from 2024. The 2015 model grouped it under stability ([DORA history][]).
- **Measures:** Counts failures caused by a change to production or a release to users. The survey asks how long it takes to restore service after such a change degrades service and requires remediation. DORA does not specify the clock's start point: the deployment, its detection, or the opening of an incident.
- **Unit:** Duration. DORA does not specify whether to aggregate with a median or a mean.
- **Survey question (2024):** "How long does it generally take to restore service after a change to production or release to users results in degraded service (for example, lead to service impairment or service outage) and subsequently require remediation (for example, require a hotfix, rollback, fix forward, or patch)?" Answers are the same six time bands as Change Lead Time, plus "I don't know or NA". The 2025 survey uses the same bands and a slightly different wording ([DORA 2024 questions][]; [DORA 2025 questions][]). The 2022 survey asked about "a service incident or a defect that impacts users" instead of a change, so its wording differs ([DORA 2022 questions][]).
- **Former names:** "mean time to recover" (MTTR), 2014 to 2015. "time to restore service" ([Accelerate][], 2018; survey headings to 2025). DORA renamed and narrowed the metric in 2023 ([DORA history][]).

## Instability

> "Instability is a measure of how well the software deployments go."
>
> DORA, [DORA's software delivery performance metrics][]

Instability contains two metrics: Change Fail Rate and Deployment Rework Rate. The 2024 report called this group "software delivery stability" ([DORA 2024 report][], pp. 11-12).

### Change Fail Rate

> "The ratio of deployments that require immediate intervention following a deployment. Likely resulting in a rollback of the changes or a "hotfix" to quickly remediate any issues."
>
> DORA, [DORA's software delivery performance metrics][]

- **Group:** Instability.
- **Measures:** Only a failure that reaches end users after production counts. A change stopped before production is not a failure ([DORA 2024 report][], p. 10, footnote 1; the footnote text is on p. 16).
- **Unit:** Percentage. The share of deployments that fail.
- **Survey question (2024):** "Approximately what percentage of changes to production or released to users result in degraded service (for example, lead to service impairment or service outage) and subsequently require remediation (for example, require a hotfix, rollback, fix forward or patch), if at all?" Answers are a number from 0% to 100%, or "I don't know or NA". The 2025 survey asks the same question. The 2022 survey asked for ranges, such as "0-15%", and from 2023 it asks for a number ([DORA 2022 questions][]; [DORA 2023 questions][]; [DORA 2024 questions][]; [DORA 2025 questions][]).
- **Former names:** None found for the metric name. DORA's reports also use "change failure rate" ([DORA 2024 report][], pp. 6, 11-14; [DORA 2025 report][], pp. 21, 139) and "change fail percentage" ([DORA 2024 report][], p. 6).

### Deployment Rework Rate

> "The ratio of deployments that are unplanned but happen as a result of an incident in production."
>
> DORA, [DORA's software delivery performance metrics][]

- **Group:** Instability.
- **Measures:** Counts unplanned deployments made in response to an incident in production. The survey asks about unplanned deployments made to address a user-facing bug, so the two wordings differ slightly. DORA does not say how to decide whether a deployment is unplanned.
- **Unit:** Percentage. The share of deployments that are unplanned.
- **Survey question (2024):** "Approximately what percentage of deployments in the last 6 months were not planned but were performed to address a user-facing bug in the application?" Answers are a number from 0% to 100%, or "I don't know or NA". The 2024 report quotes the question as asking "how many deployments", not a percentage ([DORA 2024 questions][]; [DORA 2024 report][], p. 11). The 2025 survey asks for a percentage ([DORA 2025 questions][]).
- **Former names:** None. DORA added this metric in 2024 ([DORA history][]). DORA's reports also use "rework rate" ([DORA 2024 report][], p. 11; [DORA 2025 report][], p. 13).

## Changes over time

| Year | Change |
|:-----|:-------|
| 2014 to 2015 | Four measures. From 2015, grouped as throughput and stability ([DORA history][]). |
| 2018 | [Accelerate][] names four keys. |
| 2018 to 2021 | Availability, later called reliability, is added. It is not one of today's five metrics ([DORA history][]). |
| 2022 | Change Fail Rate is asked as ranges ([DORA 2022 questions][]). |
| 2023 | Time to restore service is renamed Failed Deployment Recovery Time and limited to changes ([DORA history][]). |
| 2024 | Deployment Rework Rate is added. Failed Deployment Recovery Time moves to Throughput ([DORA 2024 report][], pp. 11-13). |
| 2025 | Same five metrics. The second group is named Instability ([DORA 2025 report][], p. 13). |

## Further reading

- [DORA's software delivery performance metrics][]: the current definitions, from DORA's dora.dev guide.
- [DORA history][]: how the metrics changed since 2014.
- [DORA 2024 questions][]: the 2024 survey questions for each metric.
- [DORA 2025 questions][]: the 2025 survey questions for each metric.
- [Measuring Software Delivery Performance][]: why DORA chose these five measures, and where the evidence stops.

[Measuring Software Delivery Performance]: {% link explanation/measuring-software-delivery-performance.md %}
[DORA's software delivery performance metrics]: https://dora.dev/guides/dora-metrics/
[DORA history]: https://dora.dev/guides/dora-metrics/history/
[DORA 2022 questions]: https://dora.dev/research/2022/questions/
[DORA 2023 questions]: https://dora.dev/research/2023/questions/
[DORA 2024 questions]: https://dora.dev/research/2024/questions/
[DORA 2025 questions]: https://dora.dev/research/2025/questions/
[DORA 2024 report]: https://dora.dev/research/2024/dora-report/
[DORA 2025 report]: https://dora.dev/research/2025/dora-report/
[Accelerate]: https://itrevolution.com/product/accelerate/
