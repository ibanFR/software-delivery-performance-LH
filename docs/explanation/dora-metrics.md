---
title: DORA Metrics
layout: default
parent: Explanation
nav_order: 1
---

# DORA Metrics
{: .no_toc }

The five metrics DORA uses to measure software delivery performance, how they group together, and the pitfalls of
using them.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Overview

[DORA] (DevOps Research and Assessment) is a long-running research program that studies the capabilities driving
software delivery and operations performance. Its research found that five metrics, read together, describe how well
a team delivers changes to an application or service.

The metrics are leading indicators of organizational performance and employee well-being, and lagging indicators of
delivery practices. Improving the practices moves the metrics, not the other way around.

## Background

DORA originally published four key metrics. They evolved into the current five: Deployment Rework Rate was added, and
mean time to restore (MTTR) was replaced by Failed Deployment Recovery Time, which focuses on recovering from failed
deployments.

## How It Works

The five metrics fall into two groups.

### Throughput

How fast changes move through the delivery process.

- **Change Lead Time**: the time it takes for a change to go from committed to version control to deployed in
  production.
- **Deployment Frequency**: the number of deployments over a given period, or the time between deployments.
- **Failed Deployment Recovery Time**: the time it takes to recover from a deployment that fails and requires
  immediate intervention.

### Instability

How often deployments go wrong.

- **Change Fail Rate**: the ratio of deployments that require immediate intervention following a deployment.
- **Deployment Rework Rate**: the ratio of deployments that are unplanned but happen as a result of an incident in
  production.

### Read them together

Top performers do well across all five metrics, and low performers do poorly. Speed and stability are not a
trade-off: teams that deploy small changes often also tend to fail less and recover faster. Looking at one group alone
hides the cost of optimizing it, such as deploying faster by skipping checks.

## Pitfalls

DORA warns against these common mistakes:

1. **Setting metrics as goals**: once a metric becomes a target, teams game it (Goodhart's law).
2. **Having one metric to rule them all**: a single metric hides the trade-offs; use several in healthy tension.
3. **Using industry as a shield**: claiming regulation or domain rules out improvement.
4. **Making disparate comparisons**: the metrics apply per application or service, not across unrelated systems.
5. **Having siloed ownership**: development, operations, and release teams should share all five metrics.
6. **Competing**: the aim is for a team to improve over time, not to rank teams against each other.
7. **Focusing on measurement at the expense of improvement**: start with conversations, the DORA Quick Check, or
   existing tools rather than costly data integrations.

## Further Reading

- [DORA's software delivery performance metrics]
- [DORA Quick Check]
- [DORA capabilities catalog]

[DORA]: https://dora.dev/
[DORA's software delivery performance metrics]: https://dora.dev/guides/dora-metrics/
[DORA Quick Check]: https://dora.dev/quickcheck/
[DORA capabilities catalog]: https://dora.dev/capabilities/
