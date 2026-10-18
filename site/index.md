---
title: Home
layout: home
nav_order: 1
---

# {{ site.title }}
{: .no_toc }

{{ site.description }}.
{: .fs-6 .fw-300 }

Welcome to the Software Delivery Performance [Learning Hour]. In about an hour, you will discover the five metrics
[DORA] uses to measure software delivery performance, describe one of them with your peers, and reflect on when the
metrics help and when they hurt.

The session runs remotely on a shared [Miro board]. Facilitators should follow the [Facilitation Guide].

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Learning Goals 🎯

Participants can:

1. Understand each DORA software delivery performance metric.
2. Understand why throughput and instability metrics belong together.
3. Spot common pitfalls when using the metrics, such as using them as targets or comparing teams.

## Connect: How would you measure it? (⏱️ 5 min)

An [Open Question] to get everyone thinking about the topic. Everyone writes sticky notes on the board answering:

> How would you measure software delivery performance?

Answers are not corrected yet. Expect measures like velocity, story points, or lines of code; the Concept phase
contrasts them with the DORA metrics.

## Concept: The five DORA metrics (⏱️ 10 min)

A short [Lecture] over the Concept frames on the board:

1. **What DORA is**: a research program studying the capabilities that drive software delivery and operations
   performance.
2. **Throughput**: Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time.
3. **Instability**: Change Fail Rate, Deployment Rework Rate.
4. **Read them together**: top performers do well across all five metrics. Speed and stability are not a trade-off.
5. **Pitfalls**: metrics as goals, relying on one metric, the industry as a shield, disparate comparisons, siloed
   ownership, competing, and measurement over improvement.

See [DORA Metrics] for the definitions and [Measuring Software Delivery Performance] for the full explanation.

## Concrete Practice: Describe one metric (⏱️ 30 min)

[Work In Pairs] in five Breakout Rooms, one DORA metric per room (⏱️ 15 min). Each room fills the Metric Card in its
frame on the board:

- **Definition**: what the metric is, in your own words.
- **How to measure it**: where the data would come from in your team.
- **What makes it go bad**: situations that make the metric worse.
- **One practice that improves it**: something a team could start doing.

Rooms put the green ready stamp on their frame when done. Back in the main room, each room presents a Readout of
about 3 minutes (⏱️ 15 min).

## Conclusions: When should you use this? (⏱️ 10 min)

A [When should you use this?] reflection. Everyone writes sticky notes on the board answering:

> When should you use these metrics? What are these metrics not used for?

The Facilitator closes by linking the answers back to the pitfalls.

## Credits

The metric definitions and pitfalls are based on the [DORA metrics guide] by DORA. The session format follows the
[Samman Coaching] Learning Hour structure.

[Learning Hour]: https://sammancoaching.org/reference/learning_hour_definition.html
[DORA]: https://dora.dev/
[DORA metrics guide]: https://dora.dev/guides/dora-metrics/
[Miro board]: https://miro.com/app/board/uXjVEYsoYBU=/
[Facilitation Guide]: {% link how-to/facilitation-guide.md %}
[DORA Metrics]: {% link reference/dora-metrics.md %}
[Measuring Software Delivery Performance]: {% link explanation/measuring-software-delivery-performance.md %}
[Open Question]: https://sammancoaching.org/activities/connect.html
[Lecture]: https://sammancoaching.org/activities/concept.html
[Work In Pairs]: https://sammancoaching.org/activities/concrete.html
[When should you use this?]: https://sammancoaching.org/activities/conclusions.html
[Samman Coaching]: https://sammancoaching.org/
