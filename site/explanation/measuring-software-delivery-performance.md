---
title: Measuring Software Delivery Performance
layout: default
parent: Explanation
nav_order: 2
---

# Measuring Software Delivery Performance
{: .no_toc }

Software Delivery Performance is hard to measure. The wrong measures can make a team worse. This page explains why DORA chose the measures it uses, what its research shows, and where that evidence stops. It is background reading for Participants in the Learning Hour.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Why measuring matters

Teams that cannot see how they deliver change find it hard to improve. A question such as "Are we getting better?" gets a vague answer when nobody shares a clear picture. A good measure gives a team something concrete to discuss and change.

Software is harder to measure than physical goods. In *Accelerate*, Nicole Forsgren, Jez Humble and Gene Kim write: "Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is invisible" (*Accelerate*, chapter 2). A factory can count parts on a shelf. Software work in progress is mostly hidden. The units of work are also arbitrary. One feature might become five tickets or one. In 2003, Martin Fowler wrote that "the reason we can't measure productivity is because we can't measure output" ([Fowler, Cannot Measure Productivity]). He also noted that a team's value may not show until years after release.

Many common measures make things worse. The book names three: lines of code, velocity and utilization. It says they fail in two ways. They count output rather than outcomes, and they focus on individuals or parts of the system rather than the whole team.

- **Lines of code** reward bloated code. The authors would prefer "a 10-line solution to a 1,000-line solution to a problem," because long code costs more to maintain.
- **Velocity** was designed for capacity planning. The book says it is "a relative and team-dependent measure, not an absolute one," so comparing teams by it misleads. When teams are judged by velocity, they "inflate their estimates." The critique is about misuse. Velocity is still a sensible tool for a team's own planning.
- **Utilization** leaves no slack. When people are busy all the time, they cannot absorb unplanned work. Citing queueing theory, the book argues that as utilization approaches 100%, lead times "approach infinity."

The book names two traits of a useful measure. It should focus on a global outcome, so that "teams aren't pitted against each other." It should focus on outcomes, not output. Its example is a development team rewarded for how fast it ships and an operations team rewarded for keeping systems steady. Each group then optimizes its own number, and the whole system gets worse. The book calls this the "wall of confusion."

## The Accelerate research

The best-known evidence comes from the State of DevOps research program. Puppet partnered on the research in its early years, from 2014 to 2017. DORA is now a program run by Google Cloud ([DORA FAQ]). Both sponsors are vendors that benefit from DevOps and cloud adoption. The 2025 report also listed vendor sponsors ([DORA 2025 sponsors]). That does not make the findings wrong, but they need independent checks, and few have been published.

The research surveys working professionals every year. Its method has four steps:

1. The survey asks standard questions about practices and outcomes, so answers can be compared across years.
2. Some things cannot be measured directly, such as culture. For these, several questions are grouped to measure one underlying idea. The book calls this a latent construct.
3. A clustering method finds natural groups of respondents. It does not know what a good answer is. The book notes that it "doesn't know what counts as a 'good' or 'bad' response." It only finds patterns.
4. Regression tests which factors predict which others.

The sample is not random. Invitations went through the authors' networks, Puppet's marketing lists and social media, and respondents were asked to refer others. Most already knew the terms used in modern delivery. The book admits this misses the weakest teams: "By not collecting data on this group, we miss a cohort that are likely performing even worse than our low performers."

The headline finding is that Software Delivery Performance predicts organizational performance. In data from 2014 to 2017, *Accelerate* reports that high performers were "twice as likely" as low performers to exceed their goals. Those goals covered profitability, market share and productivity. Organizational performance was self-rated. DORA's 2022 research adds a condition: the link depends on operational reliability ([DORA 2022 research]).

> **DORA finding, weak independent corroboration.** This link comes from DORA's own survey data and is correlational. The sources reviewed for this page did not include an independent study that reproduces it. The findings describe prediction and association, not cause.

The limits are important.

- **The data is self-reported.** DORA asks each year about "the software delivery performance of the primary application or service they work on" ([DORA 2024 report], p. 13). Respondents may want to make their team look good, so the authors asked about concrete practices. DORA's 2025 guidance says self-reported data "may be more susceptible to biases (including recall bias and social desirability bias)" ([DORA measurement frameworks]).
- **The findings are correlational.** The book says causal analysis "was not included in our research." In 2024, DORA wrote that "we didn't do longitudinal studies or a proper experiment" ([DORA 2024 report], p. 110). Still, the reports use words such as "drives" and "impacts," which invite a causal reading. The critic Keunwoo Lee makes this point too ([Lee, review of Accelerate]).
- **The benchmarks move.** In 2017, high performers deployed "200 times more frequently" than low performers. In 2024, elite teams made "182x more deployments per year" than low performers ([DORA 2024 report], p. 15). Do not compare multipliers across years.

## Why Throughput and Instability tend to move together

The book's most surprising finding is that the best teams do well on both groups. The authors write that high performers "do better at all of these measures," which they call "precisely what the Agile and Lean movements predict" (*Accelerate*, chapter 2). The finding challenges a common belief that moving faster means trading off against other goals. DORA kept the pattern in later reports. The 2024 report says these metrics "typically move together," and that the best performers do well on all four ([DORA 2024 report], p. 10).

> **DORA finding, weak independent corroboration.** This pattern comes from DORA's own survey data. Independent studies are scarce, and the one found is narrow (see below).

Why might the two groups move together? Practitioners point mainly to small batches. Smaller changes are easier to test, easier to understand and quicker to fix when something goes wrong. The book says smaller batches shorten the feedback loop and reduce risk. The continuous delivery principles also say to work in small batches ([Continuous Delivery principles]). Martin Fowler's 2011 phrase is "if it hurts, do it more often" ([Fowler, Frequency Reduces Difficulty]). Frequent practice makes each step smaller and less painful.

The 2024 report raises this idea as a hypothesis. Its authors suspected that AI tools produce larger changes, and that larger batches hurt both groups. They did not measure batch size directly ([DORA 2024 report], p. 40).

The one independent study found is Khomh and colleagues' 2012 study of Firefox's shorter release cycles. Its abstract reports that users did not see significantly more post-release bugs, and that bugs were fixed faster ([Khomh et al. 2012]). That reading comes from the abstract only. The study covers one product and release timing, not the DORA metrics. It fits the DORA claim, but it is narrower.

The pattern is an average, not a rule. Several exceptions show this.

- In the 2016 data, medium performers had a worse Change Fail Rate than low performers (*Accelerate*, chapter 2).
- Change Fail Rate did not pass the statistical tests needed to form one construct with the other metrics (*Accelerate*, chapter 3). DORA's 2024 report keeps Throughput and Instability as two related factors.
- In 2024, medium performers had a lower Change Fail Rate (10%) than high performers (20%). DORA said that calling the faster teams "high performers" was a decision. It "highlights one of the potential pitfalls of using these performance levels" ([DORA 2024 report], p. 14).
- In 2024, DORA estimated that each 25% rise in AI adoption came with about a 1.5% fall in Throughput and a 7.2% fall in "delivery stability," which means higher Instability. These are estimates with wide uncertainty ([DORA 2024 report], pp. 39-40).
- In 2025, AI adoption "now improves software delivery throughput," but it "still increases delivery instability" ([DORA 2025 report], p. 4).

The useful reading is this. On average, teams that do well on Throughput also tend to do well on Instability. Because lower Instability is better, the best teams are fast and their deployments go wrong less often. Treat this as a tendency, not a law for every team.

## The DORA framework

DORA's current framework has five metrics in two groups. Each metric's definition is on the [DORA Metrics] page.

| Group | Metrics |
|---|---|
| Throughput | Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time |
| Instability | Change Fail Rate, Deployment Rework Rate |

DORA defines the groups this way. "Throughput is a measure of how many changes can move through the system over a period of time." "Instability is a measure of how well the software deployments go" ([DORA's software delivery performance metrics]).

Failed Deployment Recovery Time sits under Throughput, which can surprise readers. DORA's 2024 report explains that Throughput "measures the speed of making updates of any kind, normal changes and changes in response to a failure" ([DORA 2024 report], p. 12). A recovery is itself a change, so it belongs with the rate of change. Instability measures how often deployments create unplanned work.

The framework has changed over time. In 2023, an earlier recovery measure was replaced by Failed Deployment Recovery Time, which counts only failures caused by a change. Deployment Rework Rate was added in 2024. The 2024 report (pp. 11-12) grouped the metrics into two factors and called the second one "software delivery stability." DORA now uses the term Instability for it ([DORA 2024 report], pp. 11-12).

DORA describes the metrics as "both leading and lagging indicators." They lead organizational performance and well-being, and they lag the practices behind them. DORA's model links capabilities to Software Delivery Performance, and then to outcomes. Like the metrics, the model is correlational.

DORA also groups teams into performance levels: Elite, High, Medium and Low. In 2024, the shares were 19%, 22%, 35% and 25%, in that order ([DORA 2024 report], p. 13). DORA does not set these levels in advance. They "emerge from the survey responses," and they are recalculated every year ([DORA 2024 report], p. 13). DORA's guidance is that "the best teams are those that achieve elite improvement, not necessarily elite performance" ([DORA 2024 report], p. 14). Read the levels as a guide to improvement, not as a ladder.

In 2025, DORA replaced the ranked levels with seven team profiles. Two examples are "Foundational challenges," which described 10% of respondents, and "Harmonious high-achiever," which described 20%. DORA says these names "are an interpretation of the data" ([DORA 2025 report], p. 16). Treat the profiles as illustrations for discussion, not as labels for a team. DORA changed the approach because the five metrics "tell you what is happening, but they don't explain why" ([DORA 2025 report], p. 14).

## Common pitfalls

DORA lists seven common pitfalls. The first seven below follow that list, and each includes the reason it does harm. The last three come from the book and from practitioners, not from DORA's list.

**Setting metrics as a goal.** When a measure becomes a target, people tend to optimize the number rather than the outcome. This idea is often called Goodhart's law. The book's 2018 advice was to ask teams to set targets for these measures. DORA now lists target-setting as its first pitfall. The book also warns that in pathological cultures, measurement becomes control. Quoting Deming, it says "whenever there is fear, you get the wrong numbers." Finster argues that the metrics are often "misapplied as standalone improvement targets," which pushes teams to ship hastily ([Finster, Misuse and Abuse of DORA Metrics]).

**Having one metric to rule them all.** A single number hides trade-offs. A team can look good on Throughput while Instability rises, as the 2025 AI findings show. Several metrics, held in tension, keep both sides in view.

**Using industry as a shield against improving.** Some teams in regulated sectors say that compliance rules out change. DORA warns against accepting that claim without checking. The harm is that the conversation ends before anyone looks for improvements.

**Making disparate comparisons.** The metrics apply to one application or service. Comparing a mobile app with a mainframe system says little about either. The book makes a similar point about velocity, which it calls "incommensurable" across teams with different contexts.

**Having siloed ownership.** If development, operations and release staff each own different numbers, the wall of confusion returns. DORA suggests that all five metrics be shared across these teams, so no group protects only its own number.

**Competing.** Ranking teams against each other encourages gaming and hides shared problems. DORA's aim is "to improve your team's performance over time, not to compete against other teams or organizations" ([DORA's software delivery performance metrics]).

**Focusing on measurement at the expense of improvement.** Teams can spend weeks on dashboards and integrations before they change anything. The data may already exist, and a conversation can be a better start. Thoughtworks warned in 2022 that data taken only from delivery pipelines misses real incidents that affect users ([Thoughtworks Technology Radar]). The numbers then say little about what users experience.

**Treating levels as a maturity model.** The book says that "maturity models are not the appropriate tool to use or mindset to have" (*Accelerate*, chapter 1). Maturity models assume that the same steps look the same in every team, and they can turn a snapshot into a permanent label.

**Measuring individuals.** The metrics are defined for an application or service, not for a person. Individual numbers invite the same gaming that targets do, and they hide the system that produces the results. The SPACE framework says developer productivity "cannot be measured by a single metric or dimension" (Forsgren et al., *ACM Queue*, 2021).

**Counting AI output.** Counting the lines of code that AI produces repeats the lines-of-code problem. In 2026, Thoughtworks' Technology Radar called measuring productivity by AI-generated lines of code misleading ([Thoughtworks Technology Radar]). This is a recent practitioner view, so weigh it accordingly.

## Reading the evidence

The research can guide what a team looks at. It does not prove that a practice will cause a result in your team. The [Facilitation Guide] shows how the Learning Hour uses these ideas.

[DORA Metrics]: {% link explanation/dora-metrics.md %}
[Facilitation Guide]: {% link how-to/facilitation-guide.md %}
[DORA's software delivery performance metrics]: https://dora.dev/guides/dora-metrics/
[DORA FAQ]: https://dora.dev/faq/
[DORA 2022 research]: https://dora.dev/research/2022/
[DORA 2024 report]: https://dora.dev/research/2024/dora-report/
[DORA 2025 report]: https://dora.dev/research/2025/dora-report/
[DORA 2025 sponsors]: https://dora.dev/research/2025/sponsors/
[DORA measurement frameworks]: https://dora.dev/research/2025/measurement-frameworks/
[Fowler, Cannot Measure Productivity]: https://martinfowler.com/bliki/CannotMeasureProductivity.html
[Fowler, Frequency Reduces Difficulty]: https://martinfowler.com/bliki/FrequencyReducesDifficulty.html
[Continuous Delivery principles]: https://continuousdelivery.com/principles/
[Khomh et al. 2012]: https://swat.polymtl.ca/~foutsekh/docs/Khomh-MSR-2012.pdf
[Lee, review of Accelerate]: https://keunwoo.com/notes/accelerate-devops/
[Finster, Misuse and Abuse of DORA Metrics]: https://reader.itrevolution.com/library/how-to-misuse-abuse-dora-metrics
[Thoughtworks Technology Radar]: https://www.thoughtworks.com/radar/techniques/dora-metrics
