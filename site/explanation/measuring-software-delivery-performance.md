---
title: Measuring Software Delivery Performance
layout: default
parent: Explanation
nav_order: 2
---

# Measuring Software Delivery Performance
{: .no_toc }

Software Delivery Performance is hard to measure. Poorly chosen measures can encourage gaming and local optimization. This page explains why DORA chose the measures it uses, what its research shows, and where that evidence stops. It is background reading for Participants in the Learning Hour.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Overview

This page explains why DORA measures Software Delivery Performance the way it does. It covers the research behind that choice, the framework it produced, and the common ways measurement goes wrong. It is written for Participants who may know little about DORA. It gives no steps to follow.

DORA reports two main findings. The best teams tend to do well on both Throughput, how many changes move through the system, and Instability, how well deployments go. Both are defined under The DORA framework. And Software Delivery Performance is associated with organizational performance. Both findings come mostly from DORA's own surveys, with few independent checks. Treat them as well-supported patterns, not as proof.

The research can guide what a team looks at. It does not prove that a practice will cause a result in your team.

## Software Delivery is hard to measure

Software delivery is hard to see. In *Accelerate*, Nicole Forsgren, Jez Humble and Gene Kim write: "Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is invisible" (*Accelerate*, chapter 2). A factory can count parts on a shelf. Software work in progress is hidden. The practitioner Kua adds: "The nature of software development means most work is knowledge work, and is therefore hard to observe" ([Kua, An Appropriate Use of Metrics]).

The units of work are arbitrary too. One feature might become five tickets or one. In 2003, Martin Fowler wrote that "the reason we can't measure productivity is because we can't measure output" ([Fowler, Cannot Measure Productivity]).

Three common measures fail for these reasons. The book names them.

- **Lines of code** reward bloated code. The authors prefer "a 10-line solution to a 1,000-line solution to a problem."
- **Velocity** was meant for capacity planning. The book says it is "a relative and team-dependent measure, not an absolute one," so comparing teams by it misleads.
- **Utilization** leaves no slack for unplanned work. Citing queueing theory, the book argues that "as utilization approaches 100%, lead times approach infinity."

## Why measuring matters

Measuring well helps a team in four ways.

**Feedback on improvement.** A team cannot tell whether it is improving without measures. DORA's 2024 report says improvement needs "feedback loops to tell you how you're progressing" ([DORA 2024 report], p. 7). The 2025 report adds that changes over time "can provide insight into whether things are improving or deteriorating" ([DORA 2025 report], p. 22).

**Improvement as an experiment.** The 2024 report describes a cycle: measure the current state, plan a change, do the work, measure again, and repeat (p. 7). The metrics test ideas. They are not verdicts.

**Shared language and ownership.** The book describes a good measure as one that "focuses on global, system-level goals, and measures outcomes that different functions must collaborate in order to improve" (*Accelerate*, chapter 2). DORA says sharing the metrics "fosters collaboration and shared ownership of the delivery process" ([DORA's software delivery performance metrics]).

**Organizational outcomes.** Software Delivery Performance predicts organizational performance. In *Accelerate* (chapter 2), high performers were twice as likely as low performers to exceed their goals for profitability, market share and productivity. The same held for noncommercial goals such as customer satisfaction, quality and achieving the organization's mission. The data comes from 2014 to 2017. DORA's 2022 research adds that the link depends on operational reliability ([DORA 2022 research]).

> **DORA finding, weak independent corroboration.** This link comes from DORA's own survey data, and organizational performance was self-rated. The sources reviewed for this page did not include an independent study that reproduces it. The findings describe prediction and association, not cause.

## What makes a good measure

*Accelerate* names two traits. A good measure focuses on a global outcome, so that "teams aren't pitted against each other." It also focuses on outcomes, not output, so it does not reward busywork. The book's "wall of confusion" shows the cost of getting this wrong. Each group optimizes its own number, and the whole system suffers.

Six further properties follow. Some rest on stronger evidence than others.

**Team or system level, not individual.** DORA's 2024 report says the metrics "should be used at the application and service levels," and "certainly not to compare individuals" (p. 74). Individual numbers invite the same gaming as targets. An InfoQ article by De Simone summarizes SPACE as warning against using activity metrics alone to reward or penalize developers ([InfoQ report of SPACE]).

**Several measures held in tension.** A single number hides trade-offs. DORA advises teams to "identify multiple metrics, including some with a healthy amount of tension between them" ([DORA's software delivery performance metrics]). The 2025 report found that AI adoption "now improves software delivery throughput" but "still increases delivery instability" (p. 4). This is an association reported by DORA, not a demonstration. The SPACE abstract says developer productivity "cannot be measured by a single metric or dimension" ([SPACE, ACM Queue]). The support for this property is medium in strength.

**Used for learning, not as a target.** When a measure becomes a target, people tend to game it. The 2025 report says "the goal is continuous learning and improvement, not necessarily achieving top software delivery performance" (p. 20). Kua warns that without a stated purpose, "people may find ways, unintentionally working against the implicit goal" ([Kua, An Appropriate Use of Metrics]).

**Leading and lagging.** DORA describes the metrics as "both leading and lagging indicators" ([DORA's software delivery performance metrics]). DORA's model places them after the practices behind them and before organizational performance. The 2025 report calls them "ultimately outcomes" (p. 14). This is DORA's model, not an independent theory.

**Comparable over time.** DORA says "the best, most insightful comparisons of software delivery performance are for the same application or service over time" ([DORA 2025 report], p. 20). The book calls velocities "incommensurable" across teams with different contexts (chapter 2). Industry benchmarks can serve as context, not as a scoreboard.

**Cheap enough to collect.** The book chose deployment frequency as a proxy for batch size. It describes deployment frequency as easy to measure and typically low in variability (chapter 2). That reasoning covers this one measure, not all four. DORA says building integrations "might not be worth the initial investment" ([DORA's software delivery performance metrics]).

## The Accelerate Research

The State of DevOps research began with Puppet, which partnered on it from 2014 to 2017. DORA is now a program run by Google Cloud ([DORA FAQ]). Both sponsors are vendors that benefit from DevOps and cloud adoption. The 2025 report also listed vendor sponsors ([DORA 2025 sponsors]). That does not make the findings wrong, but few independent checks have been published.

Each year, the research surveys working professionals. Standard questions measure ideas that cannot be observed directly, such as culture. A clustering method then finds natural groups of respondents. It "doesn't know what counts as a 'good' or 'bad' response," and the groups are recalculated each year. Regression tests which factors predict which others.

The sample is not random. Invitations went through the authors' networks, Puppet's marketing lists and social media, and respondents referred others. The book admits that the sample misses the weakest teams: "we miss a cohort that are likely performing even worse than our low performers" (chapter 15).

The headline result is described in Why measuring matters, with its caveat. Two further limits apply.

- **The data is self-reported.** Respondents describe their own teams. DORA's 2025 guidance says self-reported data "may be more susceptible to biases (including recall bias and social desirability bias)" ([DORA measurement frameworks]).
- **The findings are correlational.** The book says causal analysis "was not included in our research." In 2024, DORA wrote that "we didn't do longitudinal studies or a proper experiment" ([DORA 2024 report], p. 110). The critic Keunwoo Lee makes this point too ([Lee, review of Accelerate]).

## The DORA framework

DORA's framework has five metrics in two groups. Each definition is on the [DORA Metrics] page.

| Group | Metrics |
|---|---|
| Throughput | Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time |
| Instability | Change Fail Rate, Deployment Rework Rate |

DORA defines the groups this way. "Throughput is a measure of how many changes can move through the system over a period of time." "Instability is a measure of how well the software deployments go" ([DORA's software delivery performance metrics]). The two groups are related but statistically distinct. How they relate is covered under Throughput and Instability move together.

Failed Deployment Recovery Time sits under Throughput, which can surprise readers. DORA's 2024 report explains that Throughput "measures the speed of making updates of any kind, normal changes and changes in response to a failure" (p. 12). A recovery is itself a change.

The framework has changed. In 2023, an earlier recovery measure became Failed Deployment Recovery Time, which counts only failures caused by a change. Deployment Rework Rate was added in 2024 ([DORA history]). The 2024 report called the second group "software delivery stability" (pp. 11-12). DORA now uses the term Instability.

DORA's model links capabilities to Software Delivery Performance, and then to outcomes.

DORA also groups teams into Elite, High, Medium and Low levels. In 2024, the shares were 19%, 22%, 35% and 25% (p. 13). DORA does not set these levels in advance. They "emerge from the survey responses" and change each year (p. 13). DORA says "the best teams are those that achieve elite improvement, not necessarily elite performance" (p. 14). Read the levels as a guide to improvement, not as a ladder.

In 2025, DORA replaced the ranked levels with seven team profiles. Two examples are "Foundational challenges," which described 10% of respondents, and "Harmonious high-achiever," which described 20%. DORA says these names "are an interpretation of the data" (2025 report, p. 16). Treat them as illustrations, not labels for a team. The reason for the change is that the five metrics "tell you what is happening, but they don't explain why" (p. 14).

## Throughput and Instability move together

The book's most surprising finding is that the best teams do well on both groups. High performers "do better at all of these measures," which the authors call "precisely what the Agile and Lean movements predict" (*Accelerate*, chapter 2). DORA's 2024 report says these metrics "typically move together" (p. 10).

> **DORA finding, weak independent corroboration.** This pattern comes from DORA's own survey data. Independent studies are scarce, and the one found is narrow (see below).

The book offers small batches as a mechanism. Reducing batch size "accelerates feedback" and "reduces risk" (chapter 2). The continuous delivery principles also say to work in small batches ([Continuous Delivery principles]). Fowler's 2011 phrase is "if it hurts, do it more often" ([Fowler, Frequency Reduces Difficulty]). No controlled study isolates batch size. DORA's 2024 report only hypothesizes that batch size is involved in the AI adoption pattern described in the exceptions below (p. 40).

Independent evidence is thin. Khomh and colleagues' 2012 study of Firefox's shorter release cycles found, in its abstract, no significant rise in post-release bugs and faster bug fixes ([Khomh et al. 2012]). Only the abstract was read. The study covers one product and release timing, not the DORA metrics.

The pattern is an average, not a rule. Three exceptions show this.

- Change Fail Rate did not pass the statistical tests needed to form one construct with the other metrics (*Accelerate*, chapter 3). DORA's 2024 report keeps Throughput and Instability as related factors.
- In 2024, medium performers had a lower Change Fail Rate (10%) than high performers (20%). DORA said that ranking them was a decision that "highlights one of the potential pitfalls of using these performance levels" (p. 14).
- In 2024, DORA estimated that each 25% rise in AI adoption came with about a 1.5% fall in Throughput (pp. 39-40). It also estimated a 7.2% fall in "delivery stability," which means higher Instability. These are associations with wide uncertainty.

On average, the best teams are fast, and their deployments go wrong less often. Treat this as a tendency, not a law for every team.

## Common Pitfalls

DORA lists seven common pitfalls. The first seven below follow that list. The last five come from the book and from practitioners. Where a point is covered in full under What makes a good measure, this section refers back to it.

**Setting metrics as a goal.** The book's 2018 advice was to ask teams to set targets for these measures. DORA now lists target-setting as its first pitfall. Finster warns that the metrics are often "misapplied as standalone improvement targets" ([Finster, Misuse and Abuse of DORA Metrics]). For the learning-first alternative, see Used for learning, not as a target under What makes a good measure. Targets also do more harm where people fear the numbers; see Measure in a culture without fear.

**Having one metric to rule them all.** A team can look good on Throughput while Instability rises. See the tension property under What makes a good measure.

**Using industry as a shield against improving.** DORA notes that some teams in highly regulated industries "might claim that compliance requirements" prevent improvement ([DORA's software delivery performance metrics]). The conversation then ends before anyone looks for improvements.

**Making disparate comparisons.** The metrics apply to one application or service. Comparing a mobile app with a mainframe system says little about either. The comparable-over-time property offers the alternative.

**Having siloed ownership.** If development, operations and release staff each own different numbers, the wall of confusion returns. Shared ownership is discussed under Why measuring matters.

**Competing.** Ranking teams against each other encourages gaming and hides shared problems. DORA's aim is "to improve your team's performance over time, not to compete against other teams or organizations" ([DORA's software delivery performance metrics]).

**Focusing on measurement at the expense of improvement.** Teams can spend weeks on dashboards before they change anything. The data may already exist, and a conversation can be a better start, as described under Start with a conversation, not a dashboard. In 2022, Thoughtworks warned that pipeline-only data misses real incidents that affect users ([Thoughtworks Technology Radar]).

**Start with a conversation, not a dashboard.** The [DORA Quick Check] in a retrospective gives a team a baseline in minutes. In 2026, Thoughtworks recommended using the metrics "for team reflection and learning rather than just building complex dashboards" ([Thoughtworks Technology Radar]).

**Measure in a culture without fear.** In pathological and bureaucratic cultures, "measurement is used as a form of control, and people hide information." As Deming said, "whenever there is fear, you get the wrong numbers" (*Accelerate*, chapter 2).

**Treating levels as a maturity model.** The book says "maturity models are not the appropriate tool to use or mindset to have" (*Accelerate*, chapter 1). They assume that each maturity level looks the same in every team, and they can turn a snapshot into a permanent label.

**Measuring individuals.** See the team-or-system property under What makes a good measure.

**Counting AI output.** Counting the lines of code that AI produces repeats the lines-of-code problem. In 2026, Thoughtworks' Technology Radar called measuring productivity by AI-generated lines of code misleading ([Thoughtworks Technology Radar]). This is a recent practitioner view, and the wording was taken from a summary of the Radar entry.

## Further reading

- [Accelerate][]: the original argument for the four measures. Chapter 2 explains why output measures fail.
- [DORA's software delivery performance metrics][]: current definitions and DORA's own pitfalls.
- [DORA history][]: how the metrics changed from 2014 to 2024.
- [DORA 2024 report][]: the last report with ranked levels, and its method limits.
- [DORA 2025 report][]: the seven team profiles and the AI findings.
- [SPACE, ACM Queue][]: argues that developer productivity cannot be measured by a single metric or dimension. Read through its abstract.
- [Fowler, Cannot Measure Productivity][]: a short, pre-DORA case that output cannot be measured.
- [Kua, An Appropriate Use of Metrics][]: practical rules for using metrics without turning them into targets.
- [Finster, Misuse and Abuse of DORA Metrics][]: an independent catalogue of how DORA metrics go wrong.
- [Lee, review of Accelerate][]: an independent critique of the method. It is a personal site outside the trusted list, so read it as one critical view.
- [DORA Metrics][]: the five metrics in more detail.
- [Facilitation Guide][]: how the Learning Hour uses these ideas.

[DORA Metrics]: {% link reference/dora-metrics.md %}
[Facilitation Guide]: {% link how-to/facilitation-guide.md %}
[Accelerate]: https://itrevolution.com/product/accelerate/
[DORA's software delivery performance metrics]: https://dora.dev/guides/dora-metrics/
[DORA history]: https://dora.dev/guides/dora-metrics/history/
[DORA FAQ]: https://dora.dev/faq/
[DORA 2022 research]: https://dora.dev/research/2022/
[DORA 2024 report]: https://dora.dev/research/2024/dora-report/
[DORA 2025 report]: https://dora.dev/research/2025/dora-report/
[DORA 2025 sponsors]: https://dora.dev/research/2025/sponsors/
[DORA measurement frameworks]: https://dora.dev/research/2025/measurement-frameworks/
[SPACE, ACM Queue]: https://doi.org/10.1145/3454122.3454124
[InfoQ report of SPACE]: https://www.infoq.com/news/2021/03/space-developer-productivity
[Fowler, Cannot Measure Productivity]: https://martinfowler.com/bliki/CannotMeasureProductivity.html
[Fowler, Frequency Reduces Difficulty]: https://martinfowler.com/bliki/FrequencyReducesDifficulty.html
[Kua, An Appropriate Use of Metrics]: https://martinfowler.com/articles/useOfMetrics.html
[Continuous Delivery principles]: https://continuousdelivery.com/principles/
[Khomh et al. 2012]: https://swat.polymtl.ca/~foutsekh/docs/Khomh-MSR-2012.pdf
[Lee, review of Accelerate]: https://keunwoo.com/notes/accelerate-devops/
[Finster, Misuse and Abuse of DORA Metrics]: https://reader.itrevolution.com/library/how-to-misuse-abuse-dora-metrics
[DORA Quick Check]: https://dora.dev/quickcheck/
[Thoughtworks Technology Radar]: https://www.thoughtworks.com/radar/techniques/dora-metrics
