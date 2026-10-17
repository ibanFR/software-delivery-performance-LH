# Research: Measuring Software Delivery Performance

**Date**: 2026-10-17 | **Researcher**: nw-researcher (Nova) | **Confidence**: High (overall) | **Sources**: 19 cited

## Executive Summary

*Accelerate* (Forsgren, Humble, Kim 2018, Ch 2) argues that software delivery is hard to measure because its inventory is invisible and design and delivery overlap. Earlier productivity measures (lines of code, velocity, utilization) fail because they measure local *output* rather than a shared, global *outcome*. The book picks four measures of the *delivery* part of Lean lead time: lead time from commit to production, deployment frequency (a proxy for batch size), time to restore service, and change fail rate. Two are tempo and two are stability. Cluster analysis of survey data, which "doesn't know what counts as a 'good' or 'bad' response", found high, medium and low performers every year. High performers were better on *all* measures, so there is no trade-off between speed and stability, and they were twice as likely to exceed commercial and noncommercial organizational goals.

The method rests on psychometrics: latent constructs checked for validity and reliability, large anonymous samples, and inferential prediction. The authors state the limitations openly: cross-sectional data, snowball sampling, and a DevOps-aware population. DORA's history page [D2] shows how the measures changed. Change fail rate was a statistical outlier from 2014. MTTR became **Failed Deployment Recovery Time** in 2023, limited to failures caused by a change. **Deployment Rework Rate** was added in 2024, and the five metrics were regrouped into **Throughput** (Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time) and **Instability** (Change Fail Rate, Deployment Rework Rate). The clusters are recomputed every year. Elite appeared in 2018, was missing in 2022 and returned in 2023. In 2025 DORA replaced performance tiers with seven team profiles, and AI adoption raised Throughput while hurting stability.

For use in practice, DORA [D1], Thoughtworks [T1], SPACE [A2/I1] and the book agree on these points. Do not turn the metrics into mandated targets (Goodhart's law). Read several metrics together. Measure one application or service at a time and compare it with its own past, not with other teams. Share ownership across functions. Start with conversations or the Quick Check rather than dashboards, and remember that measurement only works in a generative culture ("whenever there is fear, you get the wrong numbers", Ch 2 quoting Deming via *Lean Enterprise*). Contested points (Conflicting Information) are the book's advice to set targets and benchmark teams, the cluster inversions of 2016 and 2024, and whether 2022's missing Elite cluster was a real shift or a sampling artefact.

## Research Methodology
**Search Strategy**: Primary source first (the full *Accelerate* chapters listed in the brief, read from the local EPUB extract), then DORA's official definitions and history (dora.dev), report announcements (cloud.google.com), DORA survey questions and FAQ, then independent industry and academic sources (ACM, Springer, martinfowler.com, Thoughtworks, InfoQ). Searches were targeted with `allowed_domains` where possible.
**Source Selection**: Types: academic, official, industry, technical_docs | Reputation: high and medium-high; one medium (RedMonk) used as pointer only | Verification: book claims cross-checked against current DORA pages; DORA claims cross-checked against independent industry sources where they exist. Same-programme sources (book, dora.dev, Google Cloud) are flagged as not independent of each other.
**Quality Standards**: Target 3 sources per claim (minimum 1 authoritative) | Average reputation 0.95 | Web content sanitised (no injected instructions found).

## Terminology mapping (book and older reports to project GLOSSARY)
See the table under "Terminology mapping" after Conflicting Information below. In brief: lead time for changes → Change Lead Time; MTTR / time to restore service → Failed Deployment Recovery Time (narrower, and in Throughput since 2024); change failure rate → Change Fail Rate; tempo → Throughput; stability → Instability (different composition).

## Findings

### Q1: Why measuring is hard; what makes a good measure; flawed alternatives

#### Finding 1.1: Software delivery is hard to measure because the inventory is invisible and design and delivery overlap
**Evidence**: "Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is invisible. Furthermore, the way we break down work is relatively arbitrary, and the design and delivery activities—particularly in the Agile software development paradigm—happen simultaneously." (Accelerate, Ch 2)
**Source**: [B1] Forsgren, Humble, Kim, *Accelerate*, Ch 2 "Measuring Performance".
**Confidence**: Medium-High (single authoritative primary source; restated by DORA, see [D2] which describes the 2014 starting point as needing to define IT performance "in quantitative terms").
**Analysis**: The book's whole programme starts by fixing the *outcome* measure before studying practices; the explanation page should open here.

#### Finding 1.2: A good measure is a global outcome, not a local output
**Evidence**: Previous productivity measures "focus on *outputs* rather than *outcomes*" and "on individual or local measures rather than team or global ones." A successful measure "should focus on a global outcome to ensure teams aren't pitted against each other" (example: rewarding development for throughput and operations for stability creates the "wall of confusion"), and "should focus on outcomes not output: it shouldn't reward people for putting in large amounts of busywork". (Accelerate, Ch 2)
**Source**: [B1] Ch 2. **Verification**: [D1] dora.dev guide (pitfall "Having siloed ownership": development, operations and release teams share all five metrics); [D1] metrics "predict better organizational performance" (i.e. are outcome-linked).
**Confidence**: High (book + DORA guidance agree).

#### Finding 1.3: Lines of code, velocity and utilization are flawed productivity measures
**Evidence** (all Accelerate Ch 2):
- *Lines of code*: "we would prefer a 10-line solution to a 1,000-line solution"; rewarding LOC "leads to bloated software", but minimising LOC is also not ideal (unreadable one-liners).
- *Velocity*: "designed to be used as a *capacity planning tool*"; as a productivity metric it is "a relative and team-dependent measure, not an absolute one" so velocities are "incommensurable" across teams; "teams inevitably work to game their velocity. They inflate their estimates and focus on completing as many stories as possible at the expense of collaboration with other teams".
- *Utilization*: "high utilization is only good up to a point"; with no slack, lead times grow; "Queue theory in math tells us that as utilization approaches 100%, lead times approach infinity".
**Source**: [B1] Ch 2. **Verification**: Goodhart-style gaming is also DORA's first pitfall [D1]; see Q7 for Forsgren et al. on the risks of single-metric productivity measures [A2].
**Confidence**: High for the argument (authoritative primary source + consistent with later DORA/SPACE guidance).
**Glossary note**: "velocity" is used here only because the book uses it as the example of a flawed measure. GLOSSARY lists "velocity" as a term to avoid for Software Delivery Performance and Throughput.

#### Finding 1.4: Focus on capabilities, not maturity models
**Evidence**: "maturity models are not the appropriate tool to use or mindset to have"; four reasons: maturity models aim to "arrive" whereas transformation is continuous improvement; they are "lock-step" and linear whereas capability models are "multidimensional and dynamic"; capability models are "outcome based" whereas maturity models measure tooling install base and "end up being vanity metrics"; maturity levels are static while "what is good enough and even 'high-performing' today is no longer good enough in the next year". (Accelerate, Ch 1)
**Source**: [B1] Ch 1. **Verification**: DORA's current guide frames the metrics as "lagging indicators" of capabilities/practices and points to the capabilities catalog [D1]; the 24 capabilities in the book's Quick Reference / Appendix A [B1].
**Confidence**: High.
**Analysis**: Relevant for the page because it explains *why* the metrics measure outcomes and the capabilities are what teams change.

### Q2: Accelerate's original four measures

#### Finding 2.1: The four measures and how the book defined them
**Evidence** (Accelerate Ch 2): "we settled on four: delivery lead time, deployment frequency, time to restore service, and change fail rate."
- **Delivery lead time**: Lean lead time has two parts, design and delivery. The design part is the "fuzzy front end" (Reinertsen 2009) where "it's often unclear when to start the clock, and often there is high variability". The *delivery* part "is easier to measure and has a lower variability". Measured as "the time it takes to go from code committed to code successfully running in production". Survey options: less than one hour / less than one day / one day to one week / one week to one month / one to six months / more than six months. Short lead times give "faster feedback" and let teams ship fixes rapidly. Table 2.1 (from Kim et al. 2016) contrasts *Product Design and Development* (estimates highly uncertain, outcomes highly variable) with *Product Delivery* (cycle times well-known and predictable, outcomes low variability).
- **Deployment frequency**: a *proxy for batch size*, since batch size "is hard to measure and communicate across contexts as there is no visible inventory"; "deployment frequency is the reciprocal of batch size" (footnote 2). "Deployment" means deployment to production or an app store. Six frequency options from "on demand (multiple deploys per day)" to "fewer than once every six months", asked "for the primary service or application they work on".
- **Time to restore service**: "failure is inevitable, so the key question becomes: How quickly can service be restored?" Asked for "the primary application or service" when a service incident (unplanned outage, service impairment) occurs.
- **Change fail rate**: "what percentage of changes to production (including, for example, software releases and infrastructure configuration changes) fail"; in Lean terms the "percent complete and accurate" of the delivery process; failure = "result in degraded service or subsequently require remediation (e.g., lead to service impairment or outage, require a hotfix, a rollback, a fix-forward, or a patch)".
**Source**: [B1] Ch 2. **Verification**: [D1] current definitions (Change Lead Time still "committed to version control to deployed in production"); [D2] history (2014 start with four variables).
**Confidence**: High.
**Terminology mapping**: book "delivery lead time" / table label "Lead Time for Changes" = **Change Lead Time**; book "time to restore service" / "MTTR" = predecessor of **Failed Deployment Recovery Time** (narrower: only failures caused by a change, see Q6); book "change fail rate" / table "Change Failure Rate" = **Change Fail Rate**. Note also Ch 14 defines lead time as commit "to code in a deployable state" whereas Ch 2 says "successfully running in production"; current DORA says "deployed in production" [D1].
**Analysis**: All four were asked about "the primary application or service" the respondent works on, which is the root of today's guidance to measure per application or service [D1].

### Q3: Tempo vs stability; no trade-off

#### Finding 3.1: Two dimensions, tempo and stability
**Evidence**: "Delivery lead times and deployment frequency are both measures of software delivery performance *tempo*." The restore and fail-rate measures were added to check whether teams improve "at the expense of the stability of the systems". (Accelerate Ch 2.) DORA's history: from 2015 the model "settled into two groups. Throughput: deployment frequency and deployment lead time. Stability: MTTR and change fail rate" [D2].
**Source**: [B1] Ch 2; [D2]. **Confidence**: High.
**Terminology mapping**: book "tempo" / 2015-2022 "throughput" vs "stability". Today's grouping is **Throughput** vs **Instability** and, importantly, recovery time moved from stability into Throughput in 2024 [D2]. The project avoids "stability" as a group name (GLOSSARY).

#### Finding 3.2: High performers do better on both; no trade-off
**Evidence**: "these results demonstrate that there is no tradeoff between improving performance and achieving higher levels of stability and quality. Rather, high performers do better at *all* of these measures." (Accelerate Ch 2.) Appendix B: "there are no trade-offs between improving performance and achieving higher levels of tempo and stability: they move in tandem." 2017 ratios (Ch 1): high vs low performers had "46 times more frequent code deployments", "440 times faster lead time from commit to deploy", "170 times faster mean time to recover", "5 times lower change failure rate". DORA guide today: "speed and stability are not tradeoffs"; "Top performers do well across all five metrics, and low performers do poorly" [D1].
**Source**: [B1] Ch 1, Ch 2, App B; [D1]; [D2] (2015 finding). **Confidence**: High.
**Analysis**: The 2017 tables (Table 2.2/2.3) used the median bucket per cluster; low performers sometimes shared medians with medium performers (asterisked) while being lower on average. Ch 2 also observed the "high-performing cluster is pulling away from the pack" and low performers losing stability in 2017 when trying to "work harder" on tempo.

### Q4: How DORA measures (surveys, latent constructs, cluster analysis)

#### Finding 4.1: Cluster analysis groups respondents without knowing what "good" is
**Evidence**: "Cluster analysis ... attempts to group responses so that responses in the same group are more similar to each other than to responses in other groups ... This technique has no understanding of the semantics of responses—in other words, it doesn't know what counts as a 'good' or 'bad' response". It gave "high, medium, and low performers", "significantly different across all four measures" every year. (Accelerate Ch 2; App B.)
**Source**: [B1] Ch 2, App B. **Verification**: [X1] quotes the same "doesn't know what counts as good or bad" description for the 2024 clusters; DORA FAQ: methods "objectively reveal clusters of similar respondents" [D6]; see Finding 6.4 and Q8 for later clustering changes. **Confidence**: High for the method description.

#### Finding 4.2: Software delivery performance as a statistical construct (and the change fail rate caveat)
**Evidence**: App B: "The software delivery performance construct is a combination of three metrics: lead time, release frequency, and MTTR. Change fail rate is not included in the construct, though it is highly correlated with the construct." DORA history: in 2014 change fail rate "did not significantly correlate with the other variables", so the 2014 definition used three metrics [D2].
**Source**: [B1] App B; [D2]. **Confidence**: High (two DORA-origin sources agree; not independent, same research programme).
**Analysis**: This is the seed of the 2024 split into Throughput and Instability factors: the failure-related measure has always behaved somewhat differently statistically.

#### Finding 4.3: Why surveys; latent constructs; psychometric validity
**Evidence**:
- Ch 14 reasons: surveys "allow you to collect and analyze data quickly"; "measuring the full stack with system data is difficult"; "measuring completely with system data is difficult"; "you can trust survey data"; "some things can only be measured through surveys". Surveys give everyone "the same items, the same words, and the same definitions", solving the problem that teams call different things "lead time" or "cycle time".
- Ch 13: "A latent construct is a way of measuring something that can't be measured directly", measured through several "manifest variables" (survey items). Constructs are checked for *discriminant validity*, *convergent validity* and *reliability* (internal consistency) before any analysis. Benefits: careful definition, several views of the data, resistance to a single bad data source. "All measures are proxies ... This is just as true of system data as it is of survey data."
- Ch 14 on trust: system data can be corrupted by one bad actor or bug; with "over 23,000 respondents" it would take "several hundred people 'lying' in a coordinated, organized way" to shift results; responses are anonymous.
- Ch 12/App B: analyses go "beyond correlation into prediction" using *inferential prediction* (e.g. partial least squares regression), used when experiments are not possible.
**Source**: [B1] Ch 13, Ch 14, App B. **Verification**: [A1] Forsgren & Kersten, "DevOps Metrics", *Communications of the ACM* / ACM Queue 2018 (survey vs system data trade-offs) — see below. **Confidence**: High.

#### Finding 4.4: Limitations acknowledged by the authors
**Evidence** (Ch 15): cross-sectional design ("data was collected at a single point in time" and "precluded us from longitudinal analysis"); nonprobability *snowball sampling* via mailing lists and social media (Puppet, Gene Kim and Jez Humble lists); target population is people familiar with DevOps, so "we miss a cohort that are likely performing even worse than our low performers"; respondents might "paint their team ... in a favorable light", mitigated by asking about concrete practices rather than labels (never "do you practice CI?").
**Source**: [B1] Ch 15. **Confidence**: High (self-reported limitations).

### Q5: Link to organizational performance

#### Finding 5.1: Software delivery performance predicts organizational and noncommercial performance
**Evidence**: Organizational performance measured as respondents' rating of relative "profitability, market share, and productivity", a scale "validated multiple times in prior research (Widener 2007)", correlated with ROI and robust to economic cycles. "High-performing organizations were consistently *twice as likely* to exceed these goals as low performers." Noncommercial goals (Cavalluzzo and Ittner 2004): high performers "twice as likely to exceed objectives in quantity of goods and services, operating efficiency, customer satisfaction, quality of products or services, and achieving organization or mission goals." App B: from 2014 follow-up with stock data, high performers in public companies "had 50% higher market capitalization growth over three years" (not replicated). (Accelerate Ch 2, App B.) DORA today: the metrics "predict better organizational performance and well-being for team members" and are "leading indicators" of them [D1].
**Source**: [B1] Ch 2, App B; [D1]. **Confidence**: High (with the caveat that organizational performance is self-reported).
**Analysis**: Arrows in the book's figures mean "predicts" (inferential), not proven causation from experiments.

### Q6: Evolution to today's five metrics

#### Finding 6.1: Timeline of the metrics (DORA's own history)
**Evidence** (Harvey, "A history of DORA's software delivery metrics", dora.dev, 2 Jan 2026 [D2]):
- 2014: four variables; change fail rate did not correlate, so "IT performance" = three metrics.
- 2015: Throughput (deployment frequency, lead time) vs Stability (MTTR, change fail rate).
- 2018: availability added; umbrella becomes "Software Delivery and Operational (SDO) performance".
- 2021: availability becomes reliability; DORA says the 2021 report "inaccurately called the 'reliability' metric the 'fifth metric'".
- 2023: MTTR / time to restore service renamed **Failed Deployment Recovery Time**, because earlier definitions "did not distinguish between a failure initiated by a software change" and external failures such as a data center outage; this aligns it "more statistically with the other delivery metrics".
- 2024: change fail rate was seen to act "as a proxy for the amount of rework a team must perform"; "To test this, they introduced a fifth metric: deployment rework rate." Five metrics grouped into two factors: Software Delivery Throughput (Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time) and Software Delivery Instability (Change Fail Rate, Deployment Rework Rate).
**Source**: [D2]; definitions [D1]. **Verification**: see 2023/2024 report evidence below.
**Confidence**: High (authoritative primary source).
**Glossary note**: the "reliability fifth metric" of 2021 is NOT one of the project's five metrics. The project's fifth metric is Deployment Rework Rate.

#### Finding 6.2: How the 2024 survey asks the five questions (still per primary application or service)
**Evidence**: DORA's published 2024 survey questions [D4]: the section preamble reads "For the primary application or service you work on..."; Change Lead Time asked as "how long does it take to go from code committed to code..." with the same six duration bands as 2014-2017; Failed Deployment Recovery Time asked as "How long does it generally take to restore service after a change to production or release to users..."; Change Fail Rate asked as a percentage of changes that "result in degraded service..."; Deployment Rework Rate is measured by "Approximately what percentage of deployments in the last 6 months were not planned but were performed to address a user-facing [bug]". Deployment Frequency asks "How often does your organization deploy code to production or release it to end users?" (organization wording; same six bands as the book).
**Source**: [D4] dora.dev 2024 Questions. **Verification**: [B1] Ch 2 (same answer bands in 2014-2017); [D2] (2023 recovery-time redefinition; 2024 rework addition). **Confidence**: High.
**Analysis**: The survey instrument has been remarkably stable: the same answer bands that appear in *Accelerate* Ch 2 are still used a decade later, which is what makes year-on-year comparison of clusters possible at all. The recovery question is now scoped to "after a change", matching the 2023 redefinition.

#### Finding 6.3: Why the changes happened (DORA's stated reasons)
**Evidence**:
- *MTTR to Failed Deployment Recovery Time (2023)*: earlier definitions "did not distinguish between a failure initiated by a software change" and external failures; the narrower definition aligns it "more statistically with the other delivery metrics" [D2].
- *Deployment Rework Rate added (2024)*: Change Fail Rate "acted as a proxy for the amount of rework a team must perform"; DORA added rework rate "to test this" [D2]. Change fail rate had been the statistical outlier since 2014 [D2], [B1 App B].
- *Throughput vs Instability (2024)*: the five metrics are grouped into two factors; recovery time is placed in Throughput [D1], [D2]. DORA's history page does not spell out a rationale for moving recovery time; an industry analyst summary reports that "the DORA team has started defining the time to recover from failure as a measure of throughput" after the rework analysis [X1, not in trusted list, pointer only].
**Source**: [D2], [D1], [B1]. **Confidence**: High for the MTTR and rework rationale; Low-Medium for the reason recovery time moved into Throughput (see Knowledge Gaps).
**Interpretation (labelled)**: Recovery time is about how fast a team can get a fix through the pipeline, i.e. the same flow capability as Change Lead Time and Deployment Frequency, while Instability measures how often deployments go wrong. This interpretation is consistent with the book's own remark that short lead times matter "when there is a defect or outage and we need to deliver a fix rapidly" (Ch 2) but is not an explicit DORA statement.

#### Finding 6.4: From four performance clusters to team profiles (2018-2025)
**Evidence**:
- *Accelerate* (2014-2017 data): three clusters, high/medium/low [B1 Ch 2].
- 2018: an "Elite" cluster appears as a subset of high performers (about 7% of respondents), reported as deploying 46 times more often than low performers, with 2,555 times faster lead times, 2,604 times faster time to restore and 7 times lower change failure rate [D7 2018 report, via search extract]. Four clusters continue through 2021; the 2021 table shows Elite Change Fail Rate 0-15% vs 16-30% for High/Medium/Low [D5 2021 report, via search extract].
- 2023: "four performance levels, including the return of the Elite performance level"; "Elite performers around the world are able to achieve both throughput and stability" [G3]. In 2023 Failed Deployment Recovery Time still sat with Change Fail Rate under *stability* [G3].
- 2022: "respondents fell into three clusters – High, Medium and Low. Unlike in years past, there was no evidence of an 'Elite' cluster"; Low rose "from 7% in 2021 to 19% in 2022", Medium "swelled to 69%"; hypothesis: the pandemic "may have hampered teams' ability to share knowledge, collaborate, and innovate". Same post also introduced operational-performance clusters Starting, Flowing, Slowing, Retiring ("Slowing" teams "do not deploy too often, but when they do, they are likely to succeed") [G1].
- 2024: four clusters again (Elite reported at ~19% in secondary summaries [X1]); see Q8 for the Medium vs High Change Fail Rate anomaly.
- 2025: "Simple software delivery metrics alone aren't sufficient. They tell you what is happening but not why it's happening. To connect performance data to experience, we conducted a cluster analysis that reveals seven common team profiles or archetypes, each with a unique interplay of performance, stability, and well-being" [G2]. Two named in the announcement: "Foundational challenges" and "Harmonious high achievers" [G2].
**Source**: [B1], [G1], [G2], [D3]. **Confidence**: High for 2022 and 2025 statements (primary Google Cloud/DORA posts); Medium for 2024 cluster shares (secondary only).
**Analysis**: Because clusters are recomputed from each year's data, the thresholds for "high" or "elite" move every year. Any "benchmark" table is a snapshot of that year's respondents, not a fixed standard.

#### Finding 6.5: AI-era findings use the Throughput/Instability split
**Evidence**: 2024: AI adoption "negatively affects software delivery stability and throughput" [D3]. 2025: "we observe a positive relationship between AI adoption on both software delivery throughput and product performance. However, AI adoption does continue to have a negative relationship with software delivery stability ... Without robust control systems, like strong automated testing, mature version control practices, and fast feedback loops, an increase in change volume leads to instability." [G2]
**Source**: [D3], [G2]. **Confidence**: Medium-High (primary, but year-specific).
**Analysis**: This is the first clear, publicly reported case where Throughput and Instability move in *different* directions for a given factor, which is a strong argument for reading the two groups separately rather than as one score (see Q8).

#### Finding 4.5: Survey data and system data are complementary
**Evidence**: Forsgren and Kersten, "DevOps Metrics: Your biggest mistake might be collecting the wrong data" (*Communications of the ACM* 61(4), 2018 / ACM Queue) frames survey measures (holistic, periodic) and system measures (continuous, limited to what tools see) as complementary [A1, Restricted Access: abstract and secondary summaries only]. *Accelerate* Ch 14: "if you ignore the perceptions and experience of the professionals working on your systems entirely, you lose an important view into your systems" [B1]. Sallin et al. (XP 2021, Springer LNBIP) note the four metrics are usually collected manually or via surveys, giving few data points, and show a prototype that measures them automatically from system data and was judged valuable by the team [A3, abstract-level]. DORA's guide today suggests starting with conversations, the DORA Quick Check, or a source-available/commercial tool with pre-built integrations; the data "is available in many existing systems" [D1].
**Source**: [A1], [A3], [B1], [D1]. **Confidence**: High for "both are valid and complementary"; full text of [A1] not verified.
**Analysis**: For Participants: DORA's research benchmarks come from surveys of thousands of people; a team improving its own delivery will often use system data from its pipeline. Both are proxies (Ch 13), and both can be gamed when used to punish (Ch 14 footnote; [A1] summary).

### Q7: Using the metrics well vs badly

#### Finding 7.1: Metrics as goals get gamed (Goodhart's law)
**Evidence**: DORA pitfall "Setting metrics as a goal": mandating targets invites teams to game the metrics, citing Goodhart's law [D1]. The common phrasing "When a measure becomes a target, it ceases to be a good measure" is Strathern's (1997) generalisation of Goodhart's 1975 remark on monetary policy [A4, bibliographic; not fetched]. *Accelerate* Ch 2 on velocity: "when velocity is used as a productivity measure, teams inevitably work to game their velocity" [B1]. Forsgren (InfoQ interview on SPACE): "Metrics influence decisions and behavior"; activity metrics "should never be used in isolation either to reward or to penalize developers"; example of a PR-turnaround SLA leading developers to ignore PRs for hours [I1]. Fowler: "false measures only make things worse" [F1].
**Source**: [D1], [B1], [I1], [F1]. **Confidence**: High (4 sources, 3 independent organisations).
**Conflict to note**: *Accelerate* Ch 2 (2018) explicitly says "ask your teams to set targets for these measures", whereas current DORA guidance lists "Setting metrics as a goal" as pitfall #1 [D1]. Reconciliation (interpretation): the book's targets are *team-chosen improvement targets* in a learning culture (same paragraph warns about pathological cultures); DORA's pitfall is about *mandated* targets. See Conflicting Information.

#### Finding 7.2: No single metric; read them together
**Evidence**: DORA pitfall "Having one metric to rule them all": complex systems need several metrics, some in tension [D1]. SPACE: "productivity cannot be reduced to a single dimension or metric"; choose "a reduced set of metrics" across individual, team and system levels [I1], [A2]. *Accelerate* Ch 13: "If only one of the data points is used as the barometer and that one data point is bad—or goes bad—we won't know it" [B1]. 2025 AI finding (Throughput up, instability up) shows why the groups must be read together [G2].
**Source**: [D1], [I1], [A2], [B1], [G2]. **Confidence**: High.

#### Finding 7.3: Measure per application or service; don't compare unlike teams or rank them
**Evidence**: DORA: the metrics "are meant to be applied at the application or service level" and "best suited for measuring one application or service at a time"; pitfalls "Making disparate comparisons" and "Competing" (the aim is improving over time, not beating other teams) [D1]. The survey has always asked about "the primary application or service you work on" [B1 Ch 2], [D4]. *Accelerate* Ch 2 on velocity: team contexts "render their velocities incommensurable" and using it to compare "inhibits collaboration between teams" [B1]. A good measure "should focus on a global outcome to ensure teams aren't pitted against each other" [B1].
Google Cloud's 2023 report announcement: "Comparing your metrics year-over-year is more meaningful than comparing yourself to other companies" [G3]. Thoughtworks Technology Radar (Adopt): use the metrics "for team reflection and learning rather than just building complex dashboards" (Apr 2026), and run the DORA Quick Check in retrospectives (Oct 2021, Mar 2022) [T1].
**Source**: [D1], [D4], [B1], [G3], [T1]. **Confidence**: High (DORA guide + book + Thoughtworks as an independent organisation).

#### Finding 7.3b: Pipeline-only measurement misses user impact
**Evidence**: Thoughtworks Radar (Oct 2021, Mar 2022): tools that compute the metrics purely from CD pipelines are "misguided"; "Stability metrics only make sense if they include data about real incidents that degrade service for the users" [T1]. *Accelerate* Ch 14: system data only sees inside the system boundary (the IBM storage "interface" story) [B1]. DORA's Change Fail Rate and Failed Deployment Recovery Time definitions hinge on "immediate intervention" and restoring service, i.e. user-facing impact [D1].
**Source**: [T1], [B1], [D1]. **Confidence**: High.
**Nuance**: *Accelerate* Ch 2 also says "We can compare and benchmark teams against the larger organizations they work in and against the wider industry". This is research benchmarking for orientation, not ranking teams for reward. See Conflicting Information.

#### Finding 7.4: Shared ownership, not siloed metrics
**Evidence**: DORA pitfall "Having siloed ownership": shared ownership of all five metrics across development, operations and release teams reduces finger-pointing [D1]. *Accelerate* Ch 2: rewarding developers for throughput and operations for stability creates the "wall of confusion"; the chosen measures are "outcomes that different functions must collaborate in order to improve" [B1].
**Source**: [D1], [B1]. **Confidence**: High.

#### Finding 7.5: Measurement depends on culture
**Evidence**: *Accelerate* Ch 2 closes: "in pathological and bureaucratic organizational cultures, measurement is used as a form of control, and people hide information ... As Deming said, 'whenever there is fear, you get the wrong numbers'" (quoting Humble et al. 2014, *Lean Enterprise*, p. 56). "Before you are ready to deploy a scientific approach to improving performance, you must first understand and develop your culture." Ch 14 footnote: collecting data "without telling everyone they must answer positively *or else*"; anonymous collection encourages honesty. Westrum's generative culture: "Messengers trained", "Failure leads to enquiry" (Ch 13 Table 13.1; Ch 3) [B1]. Forsgren & Kersten: if results are used to punish teams, data becomes unreliable [A1, secondary summary].
**Source**: [B1] Ch 2, Ch 3, Ch 13, Ch 14; [A1]. **Confidence**: Medium-High (authoritative book; [A1] only via summary).

#### Finding 7.6: Improvement over measurement; metrics as lagging indicators of capabilities
**Evidence**: DORA pitfall "Focusing on measurement at the expense of improvement": costly integrations may not be worth it at first; start with conversations or the Quick Check [D1]. The metrics are "lagging indicators for development and delivery practices" [D1]. *Accelerate* Ch 1: improve by "turning the right levers—that is, by improving the right capabilities"; 24 capabilities (Quick Reference, App A) [B1]. "Using industry as a shield" pitfall [D1] is contradicted by the book's data: "Highly regulated industries ... are also found in the high-, medium-, and low-performing groups" (App B) and system age/type did not predict performance (Ch 1) [B1].
**Source**: [D1], [B1]. **Confidence**: High.

### Q8: Contested points and conflicting findings

#### Finding 8.1: Change Fail Rate has been the statistical outlier since 2014
**Evidence**: 2014: change fail rate "did not significantly correlate with the other variables" [D2]; *Accelerate* App B: the construct is "lead time, release frequency, and MTTR. Change fail rate is not included in the construct, though it is highly correlated with the construct" [B1]. Analyst summary of 2024: "The analysis of the four key metrics has long had an outlier: change failure rate" [X1].
**Source**: [D2], [B1], [X1]. **Confidence**: High.

#### Finding 8.2: Cluster inversions (2016 and 2024)
**Evidence**: 2016: "medium performers do worse than low performers on change fail rate"; authors' hypothesis: medium performers mid-transformation doing large rearchitecture, "racking up technical debt" ("Our research doesn't conclusively explain this") — Accelerate Ch 2 "Surprise!" box; App B links this to a "J-curve" (medium performers spend 32% on unplanned work/rework vs 27% low, and do more manual deployment/change-approval work) [B1]. 2017: low performers shared medians with medium on Deployment Frequency and Lead Time (Table 2.3 asterisk) [B1]. 2024: the Medium cluster's change failure rate was lower than the High cluster's; DORA's report says the correlation between metrics "persists even in the medium performance cluster" [X1 quoting the 2024 report; primary PDF not retrieved: too large].
**Source**: [B1], [X1]. **Confidence**: High for 2016 (primary); Medium for 2024 (secondary only).

#### Finding 8.3: 2022: no Elite cluster
**Evidence**: "Unlike in years past, there was no evidence of an 'Elite' cluster"; Low 7% to 19%; Medium 69%; pandemic hypothesis; yet "this year's Low performers are a blend of last year's Low and Medium" and overall a "shift toward slightly higher software delivery performance" [G1]. DORA FAQ: data collection methods "are the same as they have been since the beginning", but "each year, there is a different (though likely overlapping) set of respondents", and some differences "may be artifacts of sampling and analysis methods" [D6].
**Source**: [G1], [D6]. **Confidence**: High (both primary).
**Analysis**: Two readings coexist: (a) a real industry shift (pandemic), or (b) sampling artefacts of a cross-sectional, snowball-sampled survey (consistent with *Accelerate* Ch 15 limitations). DORA itself holds both open.

#### Finding 8.4: "Low performers do poorly on everything" is not always true
**Evidence**: 2025 team profiles: "Foundational challenges" teams show "low performance, high system stability, and high levels of burnout and friction" [G2]. 2022 "Slowing" cluster: teams "do not deploy too often, but when they do, they are likely to succeed" [G1]. 2025: AI adoption is positively related to Throughput but negatively to stability [G2].
**Source**: [G1], [G2]. **Confidence**: Medium-High (primary, but announcement-level detail only).
**Analysis**: The "no trade-off" finding is about the population trend and the best performers (Elite/High do well on both) [B1], [D1], [G3]. It does not mean every team's metrics move together; this is why DORA asks teams to read both groups and look at the trend for their own service.

## Source Analysis

All sources accessed 2026-10-17. Reputation scores per the trusted-source config (high 1.0, medium-high 0.8, medium 0.6). Per the caller's instruction, dora.dev and cloud.google.com are treated as official/high for this topic because DORA is a Google Cloud research programme. Bias note: DORA is run by Google Cloud (a cloud vendor) and earlier reports were sponsored (e.g. Puppet's mailing lists were used for sampling, *Accelerate* Ch 15); findings about cloud and platform capabilities in particular should be read with this commercial interest in mind. The measurement-method findings used here are less exposed to that bias.

| ID | Source | URL | Domain | Type | Reputation | Verification status |
|----|--------|-----|--------|------|------------|---------------------|
| B1 | Forsgren, Humble, Kim, *Accelerate* (IT Revolution, 2018), Ch 1, 2, 3, 13, 14, 15, Quick Reference, App A, App B | (book, local EPUB extract) | n/a (book) | Academic/primary | 1.0 | Read in full (primary) |
| D1 | DORA, "DORA's software delivery performance metrics" (updated 2026-01-05) | https://dora.dev/guides/dora-metrics/ | dora.dev | Official | 1.0 | Fetched; cross-verified with B1, D2, T1 |
| D2 | Harvey, "A history of DORA's software delivery metrics" (2026-01-02) | https://dora.dev/guides/dora-metrics/history/ | dora.dev | Official | 1.0 | Fetched; cross-verified with B1 App B, G3, D4 |
| D3 | DORA, 2024 DORA Report page | https://dora.dev/research/2024/dora-report/ | dora.dev | Official | 1.0 | Fetched (summary page only) |
| D4 | DORA, 2024 survey Questions | https://dora.dev/research/2024/questions/ | dora.dev | Official | 1.0 | Fetched; consistent with B1 Ch 2 |
| D5 | DORA, 2021 Accelerate State of DevOps Report (PDF) | https://dora.dev/research/2021/dora-report/2021-dora-accelerate-state-of-devops-report.pdf | dora.dev | Official | 1.0 | Search extract only |
| D6 | DORA, FAQ (updated 2025-10-06) | https://dora.dev/faq/ | dora.dev | Official | 1.0 | Fetched |
| D7 | DORA, 2018 Accelerate State of DevOps Report | https://dora.dev/research/2018/dora-report/ | dora.dev | Official | 1.0 | Search extract only |
| G1 | DeBellis, Peters, "Announcing the 2022 Accelerate State of DevOps Report" (2022-09-29) | https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/ | cloud.google.com | Official | 1.0 | Fetched; consistent with D6 |
| G2 | Harvey, DeBellis, "Announcing the 2025 DORA Report" (2025-09-23) | https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report | cloud.google.com | Official | 1.0 | Fetched |
| G3 | DeBellis, Harvey, "2023 State of DevOps Report: Culture is everything" (2023-10-05) | https://cloud.google.com/blog/products/devops-sre/announcing-the-2023-state-of-devops-report | cloud.google.com | Official | 1.0 | Fetched; consistent with D2 |
| A1 | Forsgren, Kersten, "DevOps Metrics", *Communications of the ACM* 61(4), 2018, doi:10.1145/3159169 | https://queue.acm.org/detail.cfm?id=3182626 | acm.org | Academic | 1.0 | [Restricted Access] 403; metadata via Crossref, content via secondary summaries |
| A2 | Forsgren, Storey, Maddila, Zimmermann, Houck, Butler, "The SPACE of Developer Productivity", ACM Queue, 2021 | https://queue.acm.org/detail.cfm?id=3454124 | acm.org | Academic | 1.0 | [Restricted Access] 403; content via I1 |
| A3 | Sallin, Kropp, Anslow, Quilty, Meier, "Measuring Software Delivery Performance Using the Four Key Metrics of DevOps", XP 2021, Springer LNBIP 419, doi:10.1007/978-3-030-78098-2_7 | https://link.springer.com/chapter/10.1007/978-3-030-78098-2_7 | springer.com | Academic | 1.0 | Abstract-level (login redirect; open copy host unreachable) |
| A4 | Strathern, "'Improving ratings': audit in the British University system", *European Review* 5(3), 1997, pp. 305-321 | (bibliographic) | n/a | Academic | 1.0 | Bibliographic only, not fetched |
| I1 | De Simone, "SPACE, a New Framework to Understand and Measure Developer Productivity", InfoQ (2021-03-18) | https://www.infoq.com/news/2021/03/space-developer-productivity | infoq.com | Industry | 0.8 | Fetched; interview with A2 lead author |
| F1 | Fowler, "Cannot Measure Productivity" (2003-08-29) | https://martinfowler.com/bliki/CannotMeasureProductivity.html | martinfowler.com | Industry | 0.8 | Fetched; [Published 2003; concept remains current] |
| T1 | Thoughtworks Technology Radar, "DORA metrics" (2018-2026 entries) | https://www.thoughtworks.com/en-gb/radar/techniques/dora-metrics | thoughtworks.com | Industry | 0.8 | Fetched |
| X1 | Stephens, "DORA 2024" (RedMonk, 2024-11-26) | https://redmonk.com/rstephens/2024/11/26/dora2024/ | redmonk.com | Industry analyst | 0.6 (not in trusted list; scored medium) | Fetched; used only as pointer to 2024 report content, never as sole support for a High-confidence claim |

Reputation: High (1.0): 15 (79%) | Medium-high (0.8): 3 (16%) | Medium (0.6): 1 (5%) | **Average: 0.95**.

Independence note: B1, D1-D7 and G1-G3 are all products of the same research programme (DORA; Forsgren and Humble co-founded it). They are authoritative about *what DORA found and recommends* but are not independent confirmations of each other. Independent voices used: F1 (Fowler), T1 (Thoughtworks), I1/A2 (SPACE, partly overlapping authorship via Forsgren), A3 (Sallin et al.), X1 (RedMonk).

## Knowledge Gaps

### Gap 1: 2024 report primary text not read
**Issue**: Cluster shares, per-cluster values and the authors' own interpretation of the Medium-vs-High Change Fail Rate inversion come only from X1 and search snippets (which also disagree on the Medium share: 35% vs 22%). | **Attempted**: dora.dev 2024 PDF (exceeded 10 MB fetch limit), dora.dev 2024 report page, Google Cloud blog search. | **Recommendation**: read the "Software delivery performance" chapter of the 2024 PDF locally before quoting 2024 numbers on the page; or avoid quoting them.

### Gap 2: Explicit rationale for moving Failed Deployment Recovery Time into Throughput
**Issue**: DORA's history [D2] and guide [D1] state the 2024 grouping but not why recovery time is a Throughput measure. | **Attempted**: D1, D2, D3, X1. | **Recommendation**: check the 2024 report's methodology/factor analysis appendix. On the page, state the grouping as DORA's and label any explanation as interpretation.

### Gap 3: ACM papers (A1, A2) full text
**Issue**: queue.acm.org and dl.acm.org returned 403; claims rest on abstracts and secondary summaries. | **Recommendation**: read the PDFs before quoting them; for the page, cite them as "further reading" rather than quoting.

### Gap 4: Independent academic replication of DORA's cluster findings
**Issue**: No peer-reviewed independent replication of the "no trade-off" cluster result was located within budget. Sallin et al. [A3] address measurement, not replication. | **Recommendation**: a targeted Google Scholar search ("DORA metrics replication", "software delivery performance empirical") if the page needs an external validation statement.

### Gap 5: 2025 team profiles
**Issue**: Only two of the seven archetype names verified from a primary source [G2]; others seen only in non-trusted summaries. Whether 2025 also published Elite/High/Medium/Low benchmarks was not confirmed. | **Recommendation**: read the 2025 report chapter "Understanding your software delivery performance: A look at seven team profiles" and the dora.dev 2025 Measurement Frameworks page.

### Gap 6: 2023 report appendix on the recovery-time redefinition
**Issue**: D2 points to the 2023 appendix for detail; not read. | **Recommendation**: optional; D2 is sufficient for the page.

## Conflicting Information

### Conflict 1: Set targets for the metrics?
**Position A**: "ask your teams to set targets for these measures" — *Accelerate* Ch 2 [B1], reputation 1.0.
**Position B**: Pitfall #1 "Setting metrics as a goal" invites gaming (Goodhart's law) — DORA guide [D1], reputation 1.0; supported by I1, F1.
**Assessment**: D1 is the current, more specific guidance and is what the site follows. The positions are reconcilable: the book's sentence is immediately followed by the warning that measurement in pathological cultures becomes "a form of control" (Ch 2). Team-owned improvement targets in a generative culture differ from mandated targets. The page should present D1's position and can cite the book's culture caveat.

### Conflict 2: Compare and benchmark teams?
**Position A**: "We can compare and benchmark teams against the larger organizations they work in and against the wider industry" — *Accelerate* Ch 2 [B1].
**Position B**: Pitfalls "Making disparate comparisons" and "Competing"; metrics are for one application or service at a time [D1]; "Comparing your metrics year-over-year is more meaningful than comparing yourself to other companies" [G3].
**Assessment**: Current DORA guidance (D1, G3) prevails. Benchmarks are research snapshots to orient a team, not league tables.

### Conflict 3: Does Change Fail Rate belong with the other metrics?
**Position A**: four measures together classify performance; all clusters differ significantly on all four [B1 Ch 2].
**Position B**: the statistical construct excluded change fail rate [B1 App B]; in 2014 it did not correlate [D2]; inversions in 2016 [B1] and 2024 [X1]; in 2024 it was moved into a separate Instability factor with Deployment Rework Rate [D2].
**Assessment**: Both are DORA's own statements. Position B explains the 2024 restructure. For the page: speed and stability tend to go together, but the failure measures behave differently enough statistically to form their own group.

### Conflict 4: Where does Change Lead Time end?
**Position A**: "code committed to code successfully running in production" (Ch 2) [B1]; current DORA "committed to version control to deployed in production" [D1].
**Position B**: "time from code commit to code in a deployable state" (Ch 14) [B1].
**Assessment**: Ch 2 and D1 are the operational definitions used in the survey; Ch 14's phrasing appears in a passage about terminology confusion. Use D1.

### Conflict 5: Real shift or sampling artefact (2022 no Elite)?
**Position A**: pandemic may have "hampered teams' ability to share knowledge, collaborate, and innovate" [G1].
**Position B**: year-to-year differences "may be artifacts of sampling and analysis methods" with a different set of respondents each year [D6]; cross-sectional, snowball-sampled design [B1 Ch 15].
**Assessment**: DORA holds both; neither is settled. The safe statement is that cluster thresholds are recomputed every year and are not a fixed standard.

### Conflict 6: Recovery time: stability or throughput?
**Position A**: stability (2015-2023: "Stability: MTTR and change fail rate" [D2]; 2023 blog [G3]; book "tempo" excludes it [B1]).
**Position B**: Throughput (2024 onward) [D1], [D2].
**Assessment**: The site follows the current grouping (GLOSSARY: Throughput includes Failed Deployment Recovery Time). The page should flag that older material groups it with stability.

## Terminology mapping (book and older reports to project GLOSSARY)

| Older term (source) | Project term (GLOSSARY) | Note |
|---|---|---|
| "delivery lead time", "product delivery lead time", "Lead Time for Changes" (B1 Ch 2; survey wording D4) | **Change Lead Time** | Same span: commit to production [D1] |
| "deployment frequency" (B1) | **Deployment Frequency** | Book treats it as a proxy for batch size |
| "time to restore service", "MTTR", "mean time to recover" (B1 Ch 1, 2, App B) | **Failed Deployment Recovery Time** | Since 2023 limited to failures caused by a change [D2]; grouped in Throughput since 2024 |
| "change fail rate", "Change Failure Rate", "change fail percentage" (B1, G3, T1) | **Change Fail Rate** | Now in Instability |
| (none in book) rework / "deployments not planned ... to address a user-facing bug" (D4) | **Deployment Rework Rate** | Added 2024 [D2] |
| "tempo" (B1), "throughput" (2015-2023) | **Throughput** | 2024 Throughput also contains recovery time |
| "stability" (B1, 2015-2023) | **Instability** | Different composition: now Change Fail Rate + Deployment Rework Rate |
| "IT performance" (2014), "SDO performance" (2018-2021) | **Software Delivery Performance** | Operational performance/reliability is not part of the five |
| "velocity" (B1 Ch 2) | (avoid) | Only mention as the book's example of a flawed measure |

## Recommended outline for the explanation page

Proposed file: `docs/explanation/measuring-software-delivery-performance.md`

```
---
title: Measuring Software Delivery Performance
layout: default
parent: Explanation
nav_order: 2
---

# Measuring Software Delivery Performance
{: .no_toc }

Why software delivery is hard to measure, how DORA's research measures it, and how to use the measures to improve rather than to judge.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}
```

1. **Overview** (2-3 sentences). Software Delivery Performance is an *outcome* the team produces together; DORA's research found a way to measure it and showed it matters. Link to `{% link explanation/dora-metrics.md %}` for the five definitions (do not repeat them). Cite [B1 Ch 2], [D1].
2. **Why measuring software delivery is hard**. Invisible inventory; arbitrary work breakdown; design and delivery overlap. Lean lead time has a "fuzzy front end" (design) and a delivery part that is easier to measure and less variable, which is why Change Lead Time starts at commit. Cite [B1 Ch 2, Table 2.1].
3. **What makes a good measure**. Two criteria: a *global outcome* that teams share (not developers rewarded for speed and operations for stability, the "wall of confusion"); *outcomes, not output*. Cite [B1 Ch 2]; shared ownership [D1].
4. **Why not lines of code, velocity or utilization**. One short paragraph each, quoting the book sparingly (10-line vs 1,000-line; velocity as capacity planning tool, incommensurable, gamed; utilization near 100% means lead times approach infinity). Add Fowler's "false measures only make things worse". Cite [B1 Ch 2], [F1], [I1]. Note that the book's examples are about *velocity*, a term the site otherwise avoids.
5. **From four measures to five**. Brief timeline table: 2014 four measures (and change fail rate as outlier), 2015 throughput/stability, 2023 MTTR becomes Failed Deployment Recovery Time (change-caused failures only), 2024 Deployment Rework Rate added and Throughput/Instability factors. Include the terminology mapping table above (short form) so Participants can read the book and older reports. Cite [D2], [D1], [B1 App B], [G3]. Credit DORA.
6. **Throughput and Instability move together**. Book's "no tradeoff" quote and 2017 multipliers (46x, 440x, 170x, 5x); DORA "speed and stability are not tradeoffs". Then the caveat: the trend holds for the population and top performers, but some teams show other shapes (2022 "Slowing", 2025 "Foundational challenges"; AI raising Throughput and instability in 2025), so read both groups. Cite [B1 Ch 1, Ch 2], [D1], [G1], [G2].
7. **How DORA measures: the science**. Surveys of thousands of practitioners about "the primary application or service you work on"; same six answer bands since 2014; latent constructs and validity/reliability checks; cluster analysis that "doesn't know what counts as a 'good' or 'bad' response"; inferential prediction, not just correlation. Why survey data is trustworthy and when system data is better. Limitations: cross-sectional, snowball sampling, self-reported, clusters recomputed every year (no fixed benchmark). Cite [B1 Ch 2, 13, 14, 15, App B], [D4], [D6], [A1], [A3].
8. **Why it matters: organizational performance**. High performers twice as likely to exceed profitability, market share and productivity goals and noncommercial goals; metrics as leading indicators of organizational performance and well-being, lagging indicators of capabilities; focus on capabilities, not maturity models. Cite [B1 Ch 1, Ch 2, App B], [D1].
9. **Measuring your own team**. Measure one application or service at a time; compare with your own past, not other teams; start with a conversation or the DORA Quick Check, not a dashboard; pipeline data alone misses user impact; measurement needs a generative culture ("whenever there is fear, you get the wrong numbers"). Link to the pitfalls on the DORA Metrics page instead of repeating the list; add the book's culture angle and Goodhart's law. Cite [D1], [G3], [T1], [B1 Ch 2, Ch 14], [A4].
10. **Open questions** (short). Change Fail Rate as the statistical outlier; the 2016 and 2024 cluster inversions; no Elite cluster in 2022 (pandemic or sampling artefact). Message for Participants: the research is evolving and DORA says so itself. Cite [B1 Ch 2, App B], [D2], [G1], [D6].
11. **Further Reading**. *Accelerate* (Ch 2 and Part II); [DORA's software delivery performance metrics]; [A history of DORA's software delivery metrics]; [DORA Quick Check]; [DORA research]; SPACE paper.

Reference-style links block at the bottom, e.g.:

```
[DORA's software delivery performance metrics]: https://dora.dev/guides/dora-metrics/
[A history of DORA's software delivery metrics]: https://dora.dev/guides/dora-metrics/history/
[DORA Quick Check]: https://dora.dev/quickcheck/
[DORA research]: https://dora.dev/research/
[2022 report announcement]: https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/
[2025 report announcement]: https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report
[Cannot Measure Productivity]: https://martinfowler.com/bliki/CannotMeasureProductivity.html
[The SPACE of Developer Productivity]: https://queue.acm.org/detail.cfm?id=3454124
```

Writing notes: use GLOSSARY terms verbatim (Participant, Throughput, Instability, Change Fail Rate, Failed Deployment Recovery Time); quote the book only for short phrases with "(Accelerate, Ch N)" attribution; credit DORA wherever its definitions or pitfalls are quoted.

## Full Citations

[B1] Forsgren, N., Humble, J., Kim, G. *Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations*. IT Revolution Press. 2018. Chapters 1, 2, 3, 13, 14, 15; Quick Reference; Appendices A, B. Read from local EPUB extract 2026-10-17.
[D1] DORA (Google Cloud). "DORA's software delivery performance metrics". dora.dev. Updated 2026-01-05. https://dora.dev/guides/dora-metrics/. Accessed 2026-10-17.
[D2] Harvey, N. "A history of DORA's software delivery metrics". dora.dev. 2026-01-02. https://dora.dev/guides/dora-metrics/history/. Accessed 2026-10-17.
[D3] DORA. "2024 DORA Report". dora.dev. 2024. https://dora.dev/research/2024/dora-report/. Accessed 2026-10-17.
[D4] DORA. "DORA Research: 2024, Questions". dora.dev. 2024. https://dora.dev/research/2024/questions/. Accessed 2026-10-17.
[D5] DORA. "Accelerate State of DevOps 2021". dora.dev. 2021. https://dora.dev/research/2021/dora-report/2021-dora-accelerate-state-of-devops-report.pdf. Accessed 2026-10-17 (search extract).
[D6] DORA. "Frequently asked questions". dora.dev. Updated 2025-10-06. https://dora.dev/faq/. Accessed 2026-10-17.
[D7] DORA. "Accelerate: State of DevOps 2018". dora.dev. 2018. https://dora.dev/research/2018/dora-report/. Accessed 2026-10-17 (search extract).
[G1] DeBellis, D., Peters, C. "Announcing the 2022 Accelerate State of DevOps Report: A deep dive into security". Google Cloud Blog. 2022-09-29. https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/. Accessed 2026-10-17.
[G2] Harvey, N., DeBellis, D. "Announcing the 2025 DORA Report: State of AI-Assisted Software Development". Google Cloud Blog. 2025-09-23. https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report. Accessed 2026-10-17.
[G3] DeBellis, D., Harvey, N. "2023 State of DevOps Report: Culture is everything". Google Cloud Blog. 2023-10-05. https://cloud.google.com/blog/products/devops-sre/announcing-the-2023-state-of-devops-report. Accessed 2026-10-17.
[A1] Forsgren, N., Kersten, M. "DevOps Metrics: Your biggest mistake might be collecting the wrong data". *Communications of the ACM* 61(4) (also in ACM Queue). 2018. doi:10.1145/3159169. https://queue.acm.org/detail.cfm?id=3182626. Accessed 2026-10-17 [Restricted Access].
[A2] Forsgren, N., Storey, M.-A., Maddila, C., Zimmermann, T., Houck, B., Butler, J. "The SPACE of Developer Productivity". ACM Queue. 2021. https://queue.acm.org/detail.cfm?id=3454124. Accessed 2026-10-17 [Restricted Access].
[A3] Sallin, M., Kropp, M., Anslow, C., Quilty, J. W., Meier, A. "Measuring Software Delivery Performance Using the Four Key Metrics of DevOps". XP 2021, LNBIP 419, Springer, pp. 103-119. 2021. doi:10.1007/978-3-030-78098-2_7. https://link.springer.com/chapter/10.1007/978-3-030-78098-2_7. Accessed 2026-10-17 (abstract).
[A4] Strathern, M. "'Improving ratings': audit in the British University system". *European Review* 5(3), pp. 305-321. 1997. Bibliographic reference, not fetched.
[I1] De Simone, S. "SPACE, a New Framework to Understand and Measure Developer Productivity". InfoQ. 2021-03-18. https://www.infoq.com/news/2021/03/space-developer-productivity. Accessed 2026-10-17.
[F1] Fowler, M. "Cannot Measure Productivity". martinfowler.com. 2003-08-29. https://martinfowler.com/bliki/CannotMeasureProductivity.html. Accessed 2026-10-17.
[T1] Thoughtworks. "DORA metrics" (Technology Radar, entries Nov 2018 to Apr 2026). thoughtworks.com. https://www.thoughtworks.com/en-gb/radar/techniques/dora-metrics. Accessed 2026-10-17.
[X1] Stephens, R. "DORA 2024". RedMonk. 2024-11-26. https://redmonk.com/rstephens/2024/11/26/dora2024/. Accessed 2026-10-17 (not in trusted list; pointer only).

## Research Metadata
Examined: ~30 sources (book chapters, web pages, search results) | Cited: 19 | Cross-refs: every major claim has 2+ sources except where noted (Finding 1.1, 4.4 are single authoritative book sources; recovery-time rationale is a documented gap) | Confidence: High ~75%, Medium-High/Medium ~20%, Low ~5% | Tool failures: ACM (403 x3), Springer (login redirect), ZHAW open copy (DNS failure), 2024 DORA PDF (exceeded 10 MB) | Output: docs/research/measuring-software-delivery-performance-comprehensive-research.md
