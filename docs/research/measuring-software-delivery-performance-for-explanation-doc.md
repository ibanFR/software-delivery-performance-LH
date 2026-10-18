# Research: Measuring Software Delivery Performance (for a Diátaxis explanation page)

**Date**: 2026-10-17 | **Researcher**: nw-researcher (Nova) | **Confidence**: Medium-High overall (High on definitions, method, history and pitfalls; Medium on the research's predictive claims) | **Sources**: 36 cited (local primaries verified)

## Executive Summary

> **Source-bias caveat (read first).** About 58% of cited sources (21 of 36) come from the DORA programme itself, which counts as one source for independence (Finster, also on itrevolution.com, is independent). Its two headline claims both rest on DORA's own survey data with weak independent corroboration: (a) Software Delivery Performance predicts organizational performance, and (b) Throughput and Instability do not trade off. See Gaps 1-2. The explanation page should present both as DORA findings and keep that caveat visible.

Software delivery resists measurement. Its inventory is invisible, its units of work are arbitrary [S34 ch. 2], and the value of the work shows up late [S6]. Output and activity measures (lines of code, velocity, utilization) fail on two counts: they count output rather than outcomes, and they reward local or individual optimisation over team or system results [S34 ch. 2]. Forsgren, Humble and Kim's answer, from the State of DevOps programme (Puppet 2014-2017 [S8], DORA at Google Cloud since [S9]), was to measure a small set of outcome measures at the level of an application or service [S1]. The programme reports year after year that these measures predict organizational performance [S34 ch. 2], [S10]. The evidence is a large, multi-year, psychometrically designed survey analysed with clustering and "inferential predictive" statistics (regression) [S34 ch. 12-13]. It is also self-reported, snowball-sampled from a DevOps-familiar population (partly via Puppet's marketing lists) [S34 ch. 15], vendor-sponsored, and correlational. The authors say outright that causal analysis "was not included in our research" [S34 ch. 12], and in 2024 that "we didn't do longitudinal studies or a proper experiment" [S35 p. 110]. No independent replication of the organizational-performance link was found (Gap 1). The programme's own advice has also shifted. *Accelerate* told readers to "set targets" for the metrics [S34 ch. 2]; DORA now lists "Setting metrics as a goal" as the first pitfall [S1].

DORA's central and most counter-intuitive finding is that Throughput and Instability are not a trade-off: on average the best teams are both fast and stable [S34 ch. 2], [S35 p. 10], [S1]. DORA reports this consistently, with documented exceptions. Independent corroboration is weak: the mechanisms (small batches, fast feedback, "if it hurts, do it more often") are argued by practitioners [S23], [S24], and one independent case study (Firefox rapid releases, abstract only) is compatible [S18] (Gap 2). The exceptions:
- Change Fail Rate did not fit the four-metric construct in *Accelerate* [S34 ch. 3], and from 2024 DORA models Throughput and Instability as two correlated factors [S35 pp. 11-12].
- In 2016 medium performers were worse than low on Change Fail Rate [S34 ch. 2].
- 2022 had no elite cluster and a large "Slowing" group [S11].
- In 2024 Medium had a lower Change Fail Rate (10%) than High (20%), and DORA called ranking them a "decision" [S35 pp. 13-14].
- Per 25% increase in AI adoption, 2024 found −1.5% Throughput and higher Instability ("an estimated 7.2% reduction" in delivery stability) [S35 pp. 39-40]. In 2025 AI improved Throughput but still increased Instability [S36 p. 4].

Today DORA defines five metrics: Throughput (Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time) and Instability (Change Fail Rate, Deployment Rework Rate) [S1]. They sit inside a model where capabilities drive performance and performance drives outcomes [S13]. The 2025 report replaced ranked clusters with seven unranked team profiles, from "Foundational challenges" (10%) to "Harmonious high-achiever" (20%), because the five metrics "tell you what is happening, but they don't explain why" [S36 pp. 14-18]. Pitfalls are the best-supported area: metrics as targets (Goodhart), comparing teams or competing, measuring individuals, treating clusters as a maturity model, one-metric focus, and tooling before improvement [S1]. DORA, independent practitioners [S28], [S7] and academic work [S29], [S31] agree on them.

## Research Methodology

**Search Strategy**: Started from the authoritative definitions page (dora.dev) and DORA's metrics history. Then DORA programme publications (dora.dev year pages, FAQ, questions, Google Cloud blog, IT Revolution) and *Accelerate*-derived texts by the authors (InfoQ, IT Revolution). Then independent critiques and practitioner sources (Fowler, Thoughtworks Radar, Finster, Keunwoo Lee), and academic work (Springer XP 2021, MSR 2012, ACM Queue SPACE, arXiv on Goodhart).
**Source Selection**: Types: primary research (DORA programme), academic, practitioner, vendor (flagged). Domains checked against `.nwave/trusted-source-domains.yaml`. All DORA-programme sources are treated as one source for cross-referencing.
**Quality Standards**: Target 3 sources per claim, at least one outside DORA for High confidence. Where that is not met, it is stated per finding. Average reputation is about 0.92 (see Source Analysis).
**Local primaries (verification pass, 2026-10-17)**: The orchestrator extracted the local files to text: the *Accelerate* epub (cited by chapter as [S34]), the 2024 DORA report v. 2024.3 ([S35]) and the 2025 DORA report v. 2025.2 ([S36]). Both PDFs carry printed page numbers that match the PDF page index, so page citations are the printed numbers. Every claim that earlier rested on secondary reporting (Tacho, TechTarget, thenewstack, Lee's description of the book) has been checked against these and re-cited to the primary where possible. ACM Queue and medium.com still returned HTTP 403.

## Terminology note

Terms follow `GLOSSARY.md` verbatim. Where a source uses an older name, the quote is kept as written and the glossary term is noted in brackets:

| Older or source name | Glossary term |
|---|---|
| MTTR, mean time to restore, time to restore service | Failed Deployment Recovery Time |
| change failure rate | Change Fail Rate |
| lead time for changes | Change Lead Time |
| rework rate | Deployment Rework Rate |
| stability | Instability (DORA now measures the inverse) |

## 1. Why measuring software delivery performance matters

### Finding 1.1: Software delivery is hard to measure because its inventory is invisible and its unit of work is arbitrary
**Evidence**: *Accelerate* ch. 2 ("Measuring Performance"): "Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is invisible. Furthermore, the way we break down work is relatively arbitrary, and the design and delivery activities—particularly in the Agile software development paradigm—happen simultaneously." [S34] The 2021 IT Revolution adaptation [S3] words the first sentence as "Measuring software delivery performance is hard—in part because...". **Quote the book wording.**
**Source**: [S34] *Accelerate*, ch. 2 (primary); [S3] IT Revolution 2021 adaptation.
**Verification**: [S6] Fowler, "CannotMeasureProductivity" (2003): "the reason we can't measure productivity is because we can't measure output." Fowler also notes a time lag: the value of a team's work may not be visible until years after release.
**Confidence**: Medium-High (one DORA-programme source plus one independent practitioner source that predates DORA by 11 years and reaches the same conclusion by a different route; two sources, not three).
**Analysis**: Two different arguments meet. Fowler says output cannot be measured; DORA says the units are arbitrary and the work in progress cannot be seen. Both lead to "do not measure output". This is useful framing for the page: the difficulty is old, and DORA did not invent the critique.

### Finding 1.2: Output and activity measures fail (lines of code, velocity, utilization)
**Evidence** (*Accelerate* ch. 2, section "The Flaws in Previous Attempts to Measure Performance" [S34]):
- Framing: "Most of these measurements focus on productivity. In general, they suffer from two drawbacks. First, they focus on *outputs* rather than *outcomes.* Second, they focus on individual or local measures rather than team or global ones. Let's take three examples: lines of code, velocity, and utilization."
- Lines of code: "in reality we would prefer a 10-line solution to a 1,000-line solution to a problem. Rewarding developers for writing lines of code leads to bloated software that incurs higher maintenance costs and higher cost of change." (Footnote 1 cites the Apple Lisa "-2000 lines of code" story.)
- Velocity: "Velocity is designed to be used as a *capacity planning tool*... However, some managers have also used it as a way to measure team productivity, or even to compare teams." "First, velocity is a relative and team-dependent measure, not an absolute one. Teams usually have significantly different contexts which render their velocities incommensurable. Second, when velocity is used as a productivity measure, teams inevitably work to game their velocity. They inflate their estimates and focus on completing as many stories as possible at the expense of collaboration with other teams".
- Utilization: "Once utilization gets above a certain level, there is no spare capacity (or 'slack') to absorb unplanned work, changes to the plan, or improvement work." "Queue theory in math tells us that as utilization approaches 100%, lead times approach infinity—in other words, once you get to very high levels of utilization, it takes teams exponentially longer to get anything done."
**Source**: [S34] *Accelerate* ch. 2 (primary). [S4] Forsgren, InfoQ 2018-07-22, restates it with slightly different wording ("make comparing velocities inappropriate", "very likely to game it"). **Use the book wording.**
**Verification**: [S6] Fowler (2003) on lines of code: copy-and-paste inflates the count, good design shortens it, so "lines of code still doesn't measure output properly". [S7] Thoughtworks Technology Radar, "DORA metrics" (Apr 2026, Adopt): "Measuring productivity by lines of code generated by AI is misleading." Story points and velocity have no independent trusted source in this run (see Gap 3).
**Confidence**: Medium-High for lines of code. The book plus Fowler [S6]. The Thoughtworks Radar Apr 2026 quote [S7] is not counted toward High: Thoughtworks was a 2025 DORA sponsor, and the blip wording comes from a fetched summary that could not be checked locally. Medium for velocity and utilization (book only; the book cites queueing theory but no independent queueing-theory source was fetched).
**Analysis**: The book's velocity argument is about *misuse*. Velocity is legitimate for capacity planning and fails only when used as a productivity measure or to compare teams. That is a useful nuance for Participants who use velocity day to day.

### Finding 1.3: Good measures focus on outcomes (not output) and on team or global results (not individual or local ones)
**Evidence**: "Use measures that focus on outcomes, not output." "Use measures that optimize for global or team outcomes, not local or individual outcomes." Software delivery measures "are both outcome measures and global measures." "When you focus on global outcomes, productivity follows." [S4]
*Accelerate* ch. 2: "A successful measure of performance should have two key characteristics. First, it should focus on a global outcome to ensure teams aren't pitted against each other. The classic example is rewarding developers for throughput and operations for stability: this is a key contributor to the 'wall of confusion' in which development throws poor quality code over the wall to operations, and operations puts in place painful change management processes as a way to inhibit change. Second, our measure should focus on outcomes not output: it shouldn't reward people for putting in large amounts of busywork that doesn't actually help achieve organizational goals." [S34] The chapter concludes the measure "focuses on global, system-level goals, and measures outcomes that different functions must collaborate in order to improve." [S34]
**Source**: [S34], [S4], [S3] (all DORA programme, counted as one).
**Verification**: [S6] Fowler: "any true measure of software development productivity must be based on delivered business value." [S7] Thoughtworks Radar (Mar 2022) says the metrics came from organization-level research, so at team level they should prompt reflection on team behaviour rather than become "another set of metrics to add to the dashboard."
**Confidence**: Medium-High (DORA plus Fowler. The Radar [S7] wording comes from a fetched summary of the blips and is treated as Medium).
**Analysis**: The developers-versus-operations example is the most vivid illustration of why a local measure fails: each silo optimises its own number and the system gets worse. It also sets up section 3. Throughput and Instability are deliberately measured together so that no single group owns "speed" while another owns "safety".

### Finding 1.4: Why measure at all: software delivery performance is linked to organizational outcomes
**Evidence**: DORA describes its metrics as "both leading and lagging indicators". "Leading indicators typically signal potential future changes in a system", while "lagging indicators reflect past performance and outcomes." The metrics lead organizational performance and well-being, and lag the practices that drive them. [S1]
**Source**: [S1] DORA, "DORA's software delivery performance metrics", dora.dev. Accessed 2026-10-17.
**Verification**: See section 2 for the *Accelerate* finding behind this claim. Thoughtworks [S7] (Nov 2018, Trial) describes the metrics as a "virtuous cycle" for continuous improvement.
**Confidence**: Medium. The predictive link comes only from DORA. No independent replication was found in this run (see Gap 1).


## 2. The Accelerate research: method, findings, limits

> **Source note.** This section was verified against the *Accelerate* text ([S34], ch. 1-3, 12-15, Appendices A-C) and the 2024 report methodology chapter ([S35]).

### Finding 2.1: The programme: Puppet partnership 2014-2017, DORA with Google Cloud from 2018/2019
**Evidence**: Before 2018, "research was conducted in partnership with Puppet" as an extension of Puppet's State of DevOps research. [S8] "DORA is a program run by Google Cloud." [S9] The 2018 report was produced by DORA with Google Cloud (Google Cloud blog, 2018-08-29, by Melody Meckfessel [S5]). In 2019 Forsgren wrote, as "Research and Strategy, Google Cloud": "With six years of research and data from more than 31,000 professionals worldwide, the 2019 Accelerate State of DevOps Report is the largest and longest-running research of its kind." [S10] By 2022 the cumulative figure was "more than 33,000 professionals". [S11]
**Source**: [S8] dora.dev/research/2014; [S9] dora.dev/faq; [S10] Google Cloud blog 2019-08-23; [S11] Google Cloud blog 2022-09-29 (all DORA programme, counted as one).
**Confidence**: High for the facts of sponsorship (these are self-descriptions, which are authoritative for this kind of fact).
**Conflict**: Secondary sources disagree on when Google acquired DORA (2018 vs 2019). This was not resolved against a primary source. The page should say "since joining Google Cloud" rather than give a date.

### Finding 2.2: Method: a cross-sectional survey, psychometrics (latent constructs), cluster analysis, and "inferential predictive" analysis
**Evidence** (all from *Accelerate* [S34] unless noted):
- Population and sampling (ch. 15): The survey deliberately targeted people "already familiar with terminology used by technology professionals who use more modern software development and delivery practices". Invitations went to the authors' lists, "Puppet's marketing databases", Gene Kim's and Jez Humble's audiences, professional groups and social media. Then "referral sampling or snowball sampling", a nonprobability method. The authors concede: "By not collecting data on this group, we miss a cohort that are likely performing even worse than our low performers." They also concede that respondents "might want to paint their team or organization in a favorable light", so they asked about concrete practices (for example, whether tests run on check-in) instead of "do you do CI?".
- Why a survey (ch. 14 headings): "Surveys allow you to collect and analyze data quickly", "Measuring the full stack with system data is difficult", "You can trust survey data", "Some things can only be measured through surveys".
- Latent constructs (ch. 13): "A latent construct is a way of measuring something that can't be measured directly." The authors use them "to report good data— or at least provide a reasonable assurance that data is telling us what we think it's telling us." Appendix C lists the validity and reliability tests: Cronbach's alpha and composite reliability ≥ 0.70, plus convergent and discriminant validity.
- The Software Delivery Performance construct (ch. 3 box "The Delivery Performance Construct"): "when we tried to turn these four metrics into a *construct*, we ran into a problem: the four measures don't pass all of the statistical tests of validity and reliability. Analysis showed that only lead time, release frequency, and time to restore together form a valid and reliable construct." Change fail rate "is strongly correlated with the software delivery performance construct".
- Cluster analysis (ch. 2, ch. 12): the clustering algorithm "has no understanding of the semantics of responses—in other words, it doesn't know what counts as a 'good' or 'bad' response". Applied "in all four years", it found high, medium and low performers that "were all significantly different across all four measures." Appendix C: groups differ "at a statistically significant level (*p* < 0.10 in our research)". This confirms Lee's point about the 0.10 threshold [S12].
- Analysis type (ch. 12): "inferential predictive" analysis is "used when purely experimental design is not possible". "To avoid problems with 'fishing for data' and finding spurious correlations, hypotheses are theory driven." The methods used were "either multiple linear regression or partial least squares regression". On the higher levels: "The final levels of analysis [predictive, causal, mechanistic] were not included in our research, because we did not have the data necessary for this kind of work." Causal analysis "generally requires randomized studies."
- Today (2024 report, Methodology, pp. 109-110 [S35]): "we didn't do longitudinal studies or a proper experiment. Despite this, we think causal thinking is how we understand the world and we try our best to use emerging techniques in causal inference to provide you with good estimates. Correlation does not imply causation, but it does imply how you think about causation." The report also notes: "Our survey is capturing a moment in time, so temporal precedence is theoretical, not part of our data." 2024 sample: "nearly 3,000 working professionals"; "roughly 39,000" over the programme's life (p. 91 [S35]).
- Programme approach and openness: "applies behavioral science methodology to uncover the predictive pathways..." [S13]. Methods and questions are under Creative Commons, but there is no raw data [S9].
**Source**: [S34], [S35] (primary); [S9], [S13]; [S12] (independent critique, consistent with the book's own text).
**Confidence**: High (the method is now described from the primary text, and an independent reviewer's account matches it).
**Analysis (interpretation)**: For the page, the method in plain language is: ask many practitioners standardised questions; check statistically that groups of questions measure one underlying thing (a latent construct, such as "culture" or "Software Delivery Performance"); let statistics find natural groupings of respondents (clusters); then test which constructs predict which others. The wording "predicts" and "is associated with" is deliberate. It is not "causes".

### Finding 2.3: Key finding: Software Delivery Performance predicts organizational performance
**Evidence**: *Accelerate* ch. 2: respondents rated "their organization's relative performance across several dimensions: profitability, market share, and productivity", a scale "validated multiple times in prior research (Widener 2007)". "Analysis over several years shows that high-performing organizations were consistently *twice as likely* to exceed these goals as low performers." High performers were "also twice as likely to exceed objectives" on noncommercial goals (quantity of goods and services, operating efficiency, customer satisfaction, quality, mission goals). [S34] Note that organizational performance is also self-rated. The book tells readers the arrows in its figures "signifies a predictive relationship... You can read these arrows using the words 'drives,' 'predicts,' 'affects,' or 'impacts.'" [S34, ch. 2 box "Reading the Figures in This Book"]. This is the wording Lee objects to [S12]. *Accelerate* ch. 3: Westrum organizational culture was hypothesised to "predict both software delivery performance and organizational performance... Both of these hypotheses proved to be true." [S34] In 2014, job satisfaction was the top predictor of organizational performance [S8]. 2019: "software speed, stability, and availability contribute to organizational performance", and the report "revalidates important findings for the sixth year in a row: First, that it's possible to optimize for stability without sacrificing speed. Second, DevOps delivers value to customers and end users by impacting both commercial and non-commercial goals." [S10] 2022: "Software delivery performance's effect on organizational performance depends on operational performance (reliability)". [S14]
**Source**: [S8], [S10], [S14] (DORA programme, one source family).
**Verification**: No independent replication of the organizational-performance link was found (Gap 1). Lee judges the book's recommendations "mostly fine" but its claim of scientific validation "questionable". [S12]
**Confidence**: Medium (consistent across many years, but from one programme only).
**Analysis**: The 2022 qualification is important and often missed. Delivery performance alone does not pay off unless the service is also reliable.

### Finding 2.4: Capabilities drive delivery performance
**Evidence**: 2014 linked version control, continuous delivery, continuous integration, automated testing and a high-trust culture to higher performance. [S8] 2022: "Combining continuous delivery, loosely coupled teams, version control, and continuous integration fosters" better performance, and "The biggest predictor of an organization's application-development security practices is cultural, not technical". [S14] The Forsgren 2017 eBook covers "the key leadership, technical, architectural, and product capabilities that drive these outcomes." [S15] *Accelerate* Appendix A: "Our research has uncovered 24 key capabilities that drive improvements in software delivery performance in a statistically significant way", grouped into five categories: continuous delivery, architecture, product and process, lean management and monitoring, and cultural [S34, verified]. *Accelerate* ch. 1 also lists factors that did *not* predict performance, among them the age and technology of the application (mainframe "systems of record" vs. greenfield) and whether operations or development teams performed deployments [S34]. DORA Core "represents a distillation of DORA's most foundational findings" and "deliberately trails the research, evolving more conservatively." [S9], [S13]
**Source**: DORA programme only.
**Confidence**: Medium.
**Gap**: No independent (non-DORA) evidence was sought or found for the claim that these specific capabilities drive delivery performance. The claim rests on DORA's own regression analyses of its self-reported survey (Gap 8). The page should attribute it ("DORA's research identifies...").

### Finding 2.5: Limits of the research
**Evidence**:
- Self-report: "I don't believe that surveys alone produce an adequate signal for objectively measuring performance" [S12]. Laura Tacho on the 2024 report: "all this data is self-reported, even the software delivery metrics." [S16] (Primary confirmation: "Each year we ask survey respondents about the software delivery performance of the primary application or service they work on", 2024 p. 13 [S35].) Sallin et al. (Springer, XP 2021) note that the four metrics are "often done manually and through surveys - with only few data points" (meaning "measured"). [S17]
- Self-selection: "there is undoubtedly some unquantifiable selection effect here". [S12] The book itself concedes the sample is DevOps-familiar, drawn partly from Puppet's marketing lists, and misses a likely worse-performing cohort (ch. 15 [S34]).
- Causation: "A casual reader would reasonably conclude that the authors claim to have demonstrated causality", through words like "drives" and "impacts". [S12] The primary texts settle the substance. *Accelerate* ch. 12 says causal analysis "was not included in our research" [S34], and the 2024 report says "we didn't do longitudinal studies or a proper experiment" (p. 110 [S35]). Both, however, invite causal reading ("drives", "impacts"; "causal thinking is how we understand the world"). Humble's 2022 reply to Lee (medium.com, 403) remains unread, but it is no longer needed for this point.
- Replicability: Lee says the full questions and data were never released [S12]. DORA now publishes methods and questions under Creative Commons, but still not raw data [S9] (see Conflict 2).
- Sponsorship: Puppet (to 2017) and Google Cloud (from 2018/2019) are vendors that benefit from DevOps and cloud adoption [S8], [S9]. The 2019 report's cloud finding ("24 times more likely ... to execute on all five capabilities of cloud computing") [S10] shows where a sponsor interest and a finding overlap. That does not make the finding wrong, but it calls for independent checks.
- Cluster benchmarks move: high-versus-low multiples change a lot from year to year. 2017: "200 times more frequently", "2,555 times faster lead times" [S15]. 2024: elite versus low "127x faster lead time", "182x more deployments per year", "8x lower change failure rate", "2293x faster failed deployment recovery times" (p. 15 [S35]). Clusters are recomputed every year: "We do not set these levels in advance, rather we let them emerge from the survey responses." (p. 13 [S35])
**Confidence**: High that these limits exist (several sources including the programme's own statements). The size of their effect is unknown.
**Analysis (interpretation)**: A fair framing for Participants is: the strongest evidence available at industry scale, consistent over a decade, but correlational, self-reported, and run by vendors. Use it to choose what to look at, not as proof that a given practice will cause a given result in your team.


## 3. Why Throughput and Instability move together

### Finding 3.1: The finding as DORA states it today
**Evidence**: "DORA's research has repeatedly demonstrated that speed and stability are not tradeoffs." The metrics are correlated for most teams, and top performers do well on all five. [S1]
2019: "it's possible to optimize for stability without sacrificing speed", revalidated "for the sixth year in a row". [S10]
Original statement, *Accelerate* ch. 2: "Astonishingly, these results demonstrate that there is no tradeoff between improving performance and achieving higher levels of stability and quality. Rather, high performers do better at *all* of these measures. This is precisely what the Agile and Lean movements predict, but much dogma in our industry still rests on the false assumption that moving faster means *trading off* against other performance goals, rather than enabling and reinforcing them." Appendix B: "there are no trade-offs between improving performance and achieving higher levels of tempo and stability: they move in tandem." [S34]
2024 report p. 10: "We've observed that these metrics typically move together, the best performers do well on all four while the lowest performers do poorly." [S35]
**Source**: [S34], [S35], [S1], [S10] (DORA programme).
**Verification (independent, mechanism and partial evidence)**:
- Khomh et al., "Do Faster Releases Improve Software Quality? An Empirical Case Study of Mozilla Firefox", MSR 2012 (IEEE) [S18]. Their abstract reports that with shorter release cycles "users do not experience significantly more post-release bugs and (2) bugs are fixed faster, yet (3) users experience these bugs earlier during software execution." **[Abstract-based: the wording comes from the abstract as returned by a search; the full paper was not read.]**
- Fowler, "Is High Quality Software Worth the Cost?" (2019) [S19]: "The 'cost' of high internal quality software is negative." He calls the speed-versus-reliability choice "a false choice", but cites the State of DevOps Report for that claim, so on the DORA claim itself he is not independent.
- One more academic search in the review round (arXiv / mining-software-repositories telemetry studies of Deployment Frequency against Change Fail Rate) returned only vendor material. Nothing was added.

**Confidence**: Medium. This is a DORA finding with weak independent corroboration. Ten-plus years of DORA results are consistent on average, with documented exceptions (Finding 3.4). The single independent empirical case study, read only through its abstract, is compatible but narrower: it shows faster releases did not cost quality, not that faster teams are more stable.
**Note on terms**: Sources say "speed and stability". In glossary terms this is "Throughput and Instability": higher Throughput tends to come with *lower* Instability. Writers should say "Throughput and Instability are not a trade-off" or "the best teams are fast and stable", and avoid saying the two metrics "rise together" (Instability falls as performance improves).

### Finding 3.2: How the finding shows across report years
| Year | What the programme reported | Source |
|---|---|---|
| 2014 | Change Fail Rate "did not correlate strongly enough" to form one construct with the other three. "IT performance" used deployment frequency, lead time and MTTR [= Failed Deployment Recovery Time] | [S2] |
| 2015 | Model reframed as throughput (deployment frequency, lead time) plus stability (MTTR, change fail rate). High performers excel at both | [S2] |
| 2016 | First exception. "Observant readers will notice that medium performers do worse than low performers on change fail rate in 2016" (medium 31-45% vs low 16-30%). The authors' hypothesis: medium performers are mid-transformation, and new work is "racking up technical debt" | [S34] ch. 2 box "Surprise!", Table 2.2 |
| 2017 | High performers deploy "200 times more frequently", have "2,555 times faster lead times" and "one-third the change failure rate" of low performers. The book says low performers "lose some ground in stability" in 2017, likely from "attempts to increase tempo ('work harder!')" without fixing underlying obstacles | [S15], [S34] ch. 2 |
| 2018 | Elite subset appears. Availability added; construct renamed "Software Delivery and Operational (SDO) performance" | [S2], Google Cloud 2018 blog |
| 2019 | Stability without sacrificing speed "for the sixth year in a row"; elite at 20% | [S10] |
| 2021 | Availability broadened to reliability. The 2021 report wrongly called reliability the "fifth metric" | [S2] |
| 2022 (blog only; report not read) | "no evidence of an 'Elite' cluster". Low rose "from 7% in 2021 to 19% in 2022", Medium "swelled to 69%". Adding operational performance gives Starting / Flowing / Slowing / Retiring. "Slowing": teams that "do not deploy too often, but when they do, they are likely to succeed" (over a third of respondents) | [S11] |
| 2023 | MTTR redefined as Failed Deployment Recovery Time, covering only failures caused by a change | [S2] |
| 2024 | Rework rate added, and two factors (pp. 11-12). "Change failure rate is strongly correlated with the other three metrics but statistical tests and methods prevent us from combining all four into one factor." Rework rate and Change Fail Rate "together... create a reliable factor of software delivery stability". "More than half of the teams in our study this year show differences in software throughput and software stability." Clusters (p. 13): Elite 19%, High 22%, Medium 35%, Low 25%. Medium Change Fail Rate 10% vs High 20%. p. 14: "Within all four clusters, throughput and stability are correlated. This correlation persists even in the medium performance cluster... where throughput is lower and stability is higher than in the high performance cluster" | [S35] pp. 11-14 |
| 2024 | AI (pp. 39-40): "Contrary to our expectations, our findings indicate that AI adoption is negatively impacting software delivery performance... the effect on delivery throughput is small, but likely negative (an estimated 1.5% reduction for every 25% increase in AI adoption). The negative impact on delivery stability is larger (an estimated 7.2% reduction for every 25% increase in AI adoption)." p. 39: "throughput and software delivery stability indicators were starting to show some independence from one another" | [S35] pp. 39-40 |
| 2025 | p. 4: "AI adoption now improves software delivery throughput, a key shift from last year. However, it still increases delivery instability." p. 35 restates 2024 as "an estimated 7.2% increase in software delivery instability" (the same finding expressed as Instability). Seven team profiles replace the ranked clusters | [S36] pp. 4, 35; [S21], [S22] |

### Finding 3.3: Mechanisms offered for why speed and stability go together
**Evidence**:
- Small batches: *Accelerate* ch. 2: "Reducing batch sizes reduces cycle times and variability in flow, accelerates feedback, reduces risk and overhead, improves efficiency, increases motivation and urgency, and reduces costs and schedule growth (Reinertsen 2009)". "we settled on deployment frequency as a proxy for batch size" (footnote: "Strictly, deployment frequency is the reciprocal of batch size"). Short lead times "enable faster feedback on what we are building" and matter "when there is a defect or outage and we need to deliver a fix rapidly and with high confidence." [S34] Continuous delivery principle "Work in small batches": it "reduces the time it takes to get feedback on our work" and "makes it easier to triage and remediate problems" [S23].
- Build quality in, citing Deming: "Cease dependence on inspection to achieve quality." [S23]
- Frequency: "if it hurts, do it more often". Pain grows steeply with the gap between instances of an activity, so doing it more often cuts difficulty through smaller batches, faster feedback and more practice. [S24] Fowler, 2011.
- Internal quality: "High internal quality reduces the cost of future features." [S19]
- A test of the mechanism: in 2024 both Throughput and stability fell with AI adoption. DORA's own hypothesis (p. 40 [S35]): AI "may have caused the field to forget one of DORA's most basic principles—the importance of small batch sizes. That is, since AI allows respondents to produce a much greater amount of code in the same amount of time, it is possible, even likely, that changelists are growing in size." This is a hypothesis; batch size was not measured directly. It fits the small-batch mechanism: when batches grow, both get worse.
- 2025: "Teams working in loosely coupled architectures with fast feedback loops see gains, while those constrained by tightly coupled systems and slow processes see little or no benefit." [S21]
**Confidence**: Medium-High. The mechanisms are argued by independent practitioners (Fowler), the CD originators (Humble, a DORA co-author, so partly not independent), and the 2024 AI result as a natural experiment within DORA. No controlled study isolating batch size was found.

### Finding 3.4: Where the "move together" pattern breaks or needs nuance
**Evidence**:
1. Statistically distinct factors: In *Accelerate*, Change Fail Rate failed the construct tests, so "only lead time, release frequency, and time to restore together form a valid and reliable construct" (ch. 3 [S34]). In 2024, "statistical tests and methods prevent us from combining all four into one factor" (p. 11 [S35]). From 2024 Throughput and Instability are separate factors (pp. 11-12 [S35]; [S2]). They are correlated, not one thing.
2. 2016: medium performers had *worse* Change Fail Rate than low performers (ch. 2 "Surprise!" box [S34]). The anomaly is as old as the book.
3. 2022: no elite cluster, and a large "Slowing" group with low throughput but good stability [S11]. This rests on the Google Cloud announcement blog only; the 2022 report itself was not read (Medium confidence).
4. 2024: Medium had lower Change Fail Rate (10%) than High (20%) (p. 13 [S35]). DORA, p. 14: "Which is better, more frequent deployments or fewer failures when deploying? There may not be a universal answer to this question. It depends on the application or service being considered, the goals of the team working on that application, and most importantly the expectations of the application's users. We made a decision to call the faster teams 'high performers,' and the slower but more stable teams 'medium performers.' This decision highlights one of the potential pitfalls of using these performance levels". Ranking is a value judgement, as DORA itself says.
5. 2024: "More than half of the teams in our study this year show differences in software throughput and software stability" (p. 11 [S35]). Throughput and stability "were starting to show some independence from one another" (p. 39 [S35]).
6. 2025: AI separates the two. "AI adoption now improves software delivery throughput... However, it still increases delivery instability" (p. 4 [S36]). DORA tested whether AI's speed would offset instability through fast failure and quick repair, and "found no positive results" [S22]. 2025 profiles that break the pattern (pp. 16-17 [S36]): "High impact, low cadence" (7%), "a low-cadence delivery model characterized by low software delivery throughput and high instability"; "Foundational challenges" (10%), "low performance, high system stability" [S21].
**Confidence**: High for items 1, 2, 4, 5 and 6 (verified in *Accelerate* and the 2024/2025 reports). Medium for item 3 (2022, blog only).
**Analysis (interpretation)**: The honest claim is "on average, across a decade of data, Throughput and Instability do not trade off, and the best teams are good at both". It is not "a law" or "true for every team". DORA's own 2024 wording is the best hedge: "While the traditional association between throughput and stability has persisted, emerging evidence suggests these factors operate with sufficient independence to warrant separate consideration" (p. 39 [S35]). 2024-2025 are the first years DORA treats the divergence as a finding rather than a footnote.

### Finding 3.5: Independent critique of the trade-off claim
**Evidence**: No peer-reviewed independent replication of the cross-industry correlation was found. Lee says the clusters rest on metrics that are "incomplete and sometimes circular" [S12]. Thoughtworks warns that pipeline-only data cannot capture real failures: "Stability metrics only make sense if they include data about real incidents that degrade service for the users." [S7, Mar 2022]
**Confidence**: Low-Medium for any independent claim either way (Gap 2).


## 4. The DORA framework today

### Finding 4.1: The five metrics, quoted verbatim from DORA
Credit: definitions © DORA, "DORA's software delivery performance metrics", https://dora.dev/guides/dora-metrics/ (CC BY 4.0, Google LLC). Accessed 2026-10-17, fetched twice with identical wording [S1].

**Throughput**: "Throughput is a measure of how many changes can move through the system over a period of time."
- **Change Lead Time**: "The amount of time it takes for a change to go from committed to version control to deployed in production."
- **Deployment Frequency**: "The number of deployments over a given period or the time between deployments."
- **Failed Deployment Recovery Time**: "The time it takes to recover from a deployment that fails and requires immediate intervention."

**Instability**: "Instability is a measure of how well the software deployments go."
- **Change Fail Rate**: "The ratio of deployments that require immediate intervention following a deployment."
- **Deployment Rework Rate**: "The ratio of deployments that are unplanned but happen as a result of an incident in production."

These definitions match `GLOSSARY.md` word for word.
**Confidence**: High (authoritative primary source; it defines the terms).

### Finding 4.2: How the definitions changed
| Change | Year | Why | Source |
|---|---|---|---|
| Four candidate metrics; Change Fail Rate left out of the 2014 "IT performance" construct | 2014 | Did not correlate strongly enough | [S2] |
| Throughput / stability pairing | 2015 | Model reframed | [S2] |
| Availability added; "SDO performance" | 2018 | Operational health | [S2] |
| Availability becomes reliability ("fifth metric" label in 2021, later called an error) | 2021 | Latency, performance, scalability | [S2] |
| MTTR / "time to restore service" becomes **Failed Deployment Recovery Time** | 2023 | Earlier definitions did not separate failures caused by a change from external failures, such as a data-centre outage. The new definition counts only recovery after a change causes an impairment, which aligns it with the other delivery metrics | [S2], [S1] |
| Rework rate added (dora.dev now names it **Deployment Rework Rate**); regrouped into Throughput (incl. Failed Deployment Recovery Time) and stability/Instability | 2024 | "We have a longstanding hypothesis that the change failure rate metric works as a proxy for the amount of rework a team is asked to do." Survey item: "approximately how many deployments in the last six months were not planned but were performed to address a user-facing bug in the application?" Result: "rework rate and change failure rate are related. Together, these two metrics create a reliable factor of software delivery stability." | [S35] p. 11; [S2] |

**Why Failed Deployment Recovery Time is under Throughput (Gap 4, now closed)**: The 2024 report, p. 12 [S35]: "Change lead time, deployment frequency, and failed deployment recovery time are used when we describe software delivery throughput. This factor measures the speed of making updates of any kind, normal changes and changes in response to a failure." The stability factor "measures the likelihood deployments unintentionally lead to immediate, additional work." In short, recovery is a speed of change (the fix is itself a change), whereas Instability is about how often deployments create unplanned work.
**Naming drift (note for writers)**: The 2024 report calls the second factor "software delivery **stability**" (pp. 11-12). The 2025 report (p. 13 [S36]) and dora.dev [S1] call it "**Instability**", and DORA's own definition text is near-identical across them. The 2025 report labels the fifth metric "Rework rate" (p. 13); dora.dev calls it "Deployment rework rate". Glossary terms follow dora.dev.
**How the survey measures them (2024)**: Deployment Frequency, Change Lead Time and recovery time are asked as ranges ("Less than one hour", "Less than one day", ..., "More than six months"). Change Fail Rate and rework are asked as a percentage, 0-100%. All are self-reported, for example "Approximately what percentage of changes to production or released to users result in degraded service". [S25]
**Confidence**: High (DORA primary, self-describing).

### Finding 4.3: Performance clusters, then team profiles
**Evidence**:
- Clusters are emergent: "We have never dictated the number of clusters; they are emergent from the patterns in the data." [S9]
- The number and shares change each year: 2016-2017 three clusters (high/medium/low) [S34 ch. 2]; 2018 adds an elite subset; 2019 elite at 20% [S10]; 2022 has no elite and Low at 19%, Medium at 69% [S11].
- 2024 table (p. 13 [S35]; clustered "on the original four software delivery metrics to remain consistent with previous years"):

| Level | Change Lead Time | Deployment Frequency | Change Fail Rate | Failed Deployment Recovery Time | % respondents (89% interval) |
|---|---|---|---|---|---|
| Elite | Less than one day | On demand (multiple deploys per day) | 5% | Less than one hour | 19% (18-20%) |
| High | Between one day and one week | Between once per day and once per week | 20% | Less than one day | 22% (21-23%) |
| Medium | Between one week and one month | Between once per week and once per month | 10% | Less than one day | 35% (33-36%) |
| Low | Between one month and six months | Between once per month and once every six months | 40% | Between one week and one month | 25% (23-26%) |

- How DORA says to use them (p. 15 [S35]): "The clusters are intended to help inspire all that elite performance is achievable. More important than reaching a particular performance level, we believe that teams should focus on improving performance overall. The best teams are those that achieve elite improvement, not necessarily elite performance." The same page says industry "does not meaningfully affect performance levels".
- 2025 (pp. 14-18 [S36]): The five metrics "are ultimately outcomes. They tell you what is happening, but they don't explain why." So DORA "conducted a cluster analysis" on eight factors (team performance, product performance, Throughput, Instability, individual effectiveness, valuable work, friction, burnout) to "reveal seven common team profiles". The seven, with share of respondents:
  1. Foundational challenges: 10%
  2. The legacy bottleneck: 11%
  3. Constrained by process: 17%
  4. High impact, low cadence: 7%
  5. Stable and methodical: 15%
  6. Pragmatic performers: 20%
  7. Harmonious high-achiever: 20%

  Caveat on p. 16: "The names and descriptions for each of these clusters are an interpretation of the data. Your team may see similar performance levels as a given cluster but may not feel the cluster name or description describe your team well."
**Confidence**: High (all verified in primary reports).
**Analysis (interpretation)**: DORA's stated reason for the 2025 change (p. 14) is that delivery metrics alone show *what*, not *why*. Profiles add well-being and environment. They are not ranked, which matches the long-standing warning against treating clusters as levels. Gap 5 is closed.

### Finding 4.4: The wider model: capabilities lead to performance, which leads to outcomes
**Evidence**: The research "applies behavioral science methodology to uncover the predictive pathways which connect ways of working, via software delivery performance, to organizational goals and individual well-being." [S13] The metrics are "leading indicators" of organizational performance and well-being, and "lagging indicators" of practices [S1]. The capabilities catalogue lists 34 capabilities (e.g. continuous integration, trunk-based development, loosely coupled teams, generative organizational culture, working in small batches, well-being, and AI-era items such as "Clear and communicated AI stance"). Together they foster "a learning environment, efficient processes, and rapid feedback, all of which accelerate software delivery and enhance overall organizational performance" [S26]. *Accelerate* (2018) listed 24 capabilities in five categories (Appendix A [S34], verified). 2024's improvement guidance (p. 16 [S35]): identify the primary application or service, gather the cross-functional team to agree a baseline (Quick Check), find impediments (value stream mapping), plan an improvement on a capability, do the work, re-evaluate, repeat.
2022 adds a moderator: delivery performance's effect on organizational performance "depends on operational performance (reliability)" [S14].
2025 adds AI as amplifier: "AI doesn't fix a team; it amplifies what's already there." Also: "Simple software delivery metrics alone aren't sufficient. They tell you what is happening but not why it's happening." [S21]
2025 measurement frameworks: DORA says "We are not here to recommend one framework over others". It suggests pairing the delivery metrics with a product framework such as H.E.A.R.T., warns "It is also a common misconception that logs-based metrics are objective", and notes that self-reported data "may be more susceptible to biases (including recall bias and social desirability bias)" [S27].
**Confidence**: High as a description of DORA's model (primary). Medium as a validated causal model (correlational, single programme).
**Recommended improvement loop (DORA)**: reduce batch sizes, set a baseline with the Quick Check, map the delivery process, commit to improving the main bottleneck, repeat [S1].


## 5. Common pitfalls

DORA's own list [S1] is the anchor. Its headings, verbatim: "Setting metrics as a goal." "Having one metric to rule them all." "Using industry as a shield against improving." "Making disparate comparisons." "Having siloed ownership." "Competing." "Focusing on measurement at the expense of improvement."

### Finding 5.1: Metrics as targets (Goodhart) and gaming
**Evidence**: DORA: "Setting metrics as a goal." "Ignoring Goodhart's law and making broad statements like, 'Every application must deploy multiple times per day…'" [S1]. *Accelerate* ch. 2 on velocity: "when velocity is used as a productivity measure, teams inevitably work to game their velocity" [S34]. *Accelerate* ch. 2 on culture and measurement: "in pathological and bureaucratic organizational cultures, measurement is used as a form of control, and people hide information that challenges existing rules, strategies, and power structures. As Deming said, 'whenever there is fear, you get the wrong numbers'" (quoting Humble et al. 2014) [S34]. Finster: the metrics are "often misapplied as standalone improvement targets", which leads to "deploying code hastily at the expense of quality" [S28]. DORA 2023: "Teams should prioritize learning and adapting based on feedback rather than solely focusing on hitting performance targets." [S32] Academic framing: "There are several distinct failure modes for overoptimization of systems on the basis of metrics"; "The importance of Goodhart effects depends on the amount of power directed towards optimizing the proxy" [S31].
**Confidence**: High (DORA, an independent practitioner, and an academic source).
**Conflict to know about**: *Accelerate* ch. 2 itself told readers to "ask your teams to set targets for these measures" (and to "Use Table 2.3 to discover where in our taxonomy you fall") [S34]. Current DORA guidance lists "Setting metrics as a goal" as the first pitfall [S1]. See Conflict 6.
**Note**: The popular wording "When a measure becomes a target, it ceases to be a good measure" is Marilyn Strathern's 1997 paraphrase, not Goodhart's original 1975 wording. No trusted source quoting either wording was fetched in this run, so attribute it carefully or paraphrase.

### Finding 5.2: Comparing teams, leaderboards, competing
**Evidence**: "These metrics are meant to be applied at the application or service level." Comparing unrelated applications, such as a mobile app and a mainframe system, misleads. "The goal is to improve your team's performance over time, not to compete against other teams or organizations." Blending metrics across teams or organizations can be problematic. [S1] "Metrics are most effective as indicators of progress when used by teams to improve their own unique process and outcomes rather than for comparing teams to each other." [S28] Velocity comparisons: "Teams usually have significantly different contexts which render their velocities incommensurable." [S34 ch. 2] 2024 report p. 16: "Each application or service has its own unique context." [S35] Thoughtworks: the metrics came from organization-level research; at team level they should prompt reflection, not become "another set of metrics to add to the dashboard" [S7].
**Confidence**: High without counting [S7]: DORA plus Finster [S28], an independent practitioner. The Radar wording [S7] is Medium (fetched blip summary).
**Note**: No trusted source uses the word "leaderboard". The point is covered by "Competing" [S1]. A widely quoted leaderboard line attributed to Martin Thwaites appears only in non-trusted secondary sources.

### Finding 5.3: Measuring individuals
**Evidence**: Finster warns against "the pitfalls of measuring individuals" [S28]. *Accelerate* ch. 2: earlier measures fail because "they focus on individual or local measures rather than team or global ones" [S34]; the InfoQ restatement: "optimize for global or team outcomes, not local or individual outcomes" [S4]. SPACE: "Developer productivity is about more than an individual's activity levels ... and it cannot be measured by a single metric or dimension." [S29] DORA's metrics are defined per application or service, not per person [S1].
**Confidence**: Medium-High. DORA's guide does not list "measuring individuals" as a pitfall in so many words; it follows from the service-level definition.

### Finding 5.4: Treating the clusters as a maturity model
**Evidence**: *Accelerate* ch. 1, "Focus on Capabilities, Not Maturity" [S34]: "we cannot stress enough that maturity models are not the appropriate tool to use or mindset to have." Maturity models help an organization "'arrive' at a mature state and then declare themselves done". They are "quite often a 'lock-step' or linear formula" and "assume that 'Level 1' and 'Level 2' look the same across all teams and organizations". They "measure the technical proficiency or tooling install base... without tying it to outcomes. These end up being vanity metrics". They "define a static level", whereas "what is good enough and even 'high-performing' today is no longer good enough in the next year." (TechTarget [S30] carries the same excerpt and is now redundant.) 2024 report: ranking Medium below High "highlights one of the potential pitfalls of using these performance levels: Improving should be more important to a team than reaching a particular performance level. The best teams are those that achieve elite improvement, not necessarily elite performance." (p. 14, repeated p. 15 [S35]). Clusters are recomputed every year (p. 13 [S35]; [S9]). Tacho (vendor) concurs: "these clusters are not a maturity model." [S16]
**Confidence**: High (book and 2024 report primary, plus independent commentary).

### Finding 5.5: Measuring in isolation from capabilities, and focusing on one metric
**Evidence**: "Having one metric to rule them all." "Attempting to measure complex systems with the idea that only one metric matters." DORA recommends several metrics with some healthy tension between them [S1]. 2025: "Simple software delivery metrics alone aren't sufficient. They tell you what is happening but not why it's happening." [S21] The report itself: "While these five metrics provide a vital snapshot of performance, they are ultimately outcomes. They tell you what is happening, but they don't explain why. A low deployment frequency might be caused by technical debt, bureaucratic processes, or team burnout—and the metrics alone can't distinguish between them." (p. 14 [S36]) 2023: "Using metrics to understand strengths and weaknesses is a starting point." [S32] Finster: DORA metrics "must be balanced with other measures of effectiveness, sustainability, flow, and culture." [S28] SPACE: no single metric or dimension [S29].
**Confidence**: High.

### Finding 5.6: Tooling-first and pipeline-only measurement
**Evidence**: "Focusing on measurement at the expense of improvement." The data is already available in many places, and conversations, the DORA Quick Check, or existing tools may be a better start [S1]. Thoughtworks (Oct 2021 / Mar 2022): misguided approaches built purely on CD pipeline data. "Stability metrics only make sense if they include data about real incidents that degrade service for the users". Take the Quick Check in retrospectives before spending weeks on dashboards [S7]. DORA 2025: "It is also a common misconception that logs-based metrics are objective." [S27] Sallin et al. show automated measurement is feasible and useful for a team, so tooling is not wrong in itself, only premature when it comes first [S17].
**Confidence**: Medium-High. DORA is primary. The Thoughtworks Radar quotes [S7] are Medium: they come from a fetched summary of the blips and are not verifiable locally. Sallin et al. [S17] (abstract only) is the only fully independent academic source, and it addresses feasibility, not ordering.

### Finding 5.7: Other DORA-listed pitfalls (siloed ownership; industry as a shield)
**Evidence**: Sharing all five metrics across development, operations and release teams "fosters collaboration and shared ownership". Some teams in highly regulated industries "might claim that compliance requirements" prevent improvement [S1]. This links back to the developers-versus-operations "wall of confusion" [S3].
**Confidence**: Medium (DORA only, though consistent with Finding 1.3).

### Finding 5.8: Newer pitfall: AI-era volume metrics
**Evidence**: "Measuring productivity by lines of code generated by AI is misleading." Rising rework rate is an early warning of blind spots, technical debt, and risks from unchecked AI-assisted development [S7, Apr 2026]. DORA 2025: 90% of respondents use AI and "more than 80%" believe it has increased their productivity, while 30% "report little to no trust in the code generated by AI" (p. 4 [S36]). Yet AI "still increases delivery instability" (p. 4 [S36]).
**Confidence**: Medium.


## Source Analysis

| ID | Source | Domain | Tier / score | Independent of DORA? | Verification status | Bias notes |
|---|---|---|---|---|---|---|
| S1 | DORA metrics guide | dora.dev | primary 1.0 | No | Fetched x2 | Google Cloud programme |
| S2 | Harvey, metrics history (2026-01-02) | dora.dev | primary 1.0 | No | Fetched | Same |
| S3 | Forsgren/Humble/Kim, four key metrics (2021) | itrevolution.com | primary 1.0 | No | Fetched | Book publisher |
| S4 | Forsgren, InfoQ (2018-07-22) | infoq.com | practitioner 0.8 | No (DORA author) | Fetched | Promotes book |
| S5 | Meckfessel, Google Cloud blog 2018 report (2018-08-29) | cloud.google.com | primary 1.0 | No | Search snippet only | Sponsor |
| S6 | Fowler, CannotMeasureProductivity (2003) | martinfowler.com | practitioner 0.8 | Yes | Fetched | Thoughtworks employee |
| S7 | Thoughtworks Radar, DORA metrics (2018-2026) | thoughtworks.com/radar | practitioner 0.8 | Yes up to 2022; weaker for 2025-26 (Thoughtworks was a 2025 DORA platinum sponsor [S33]) | Fetched (summary of blips) | Consultancy |
| S8 | DORA 2014 research page | dora.dev | primary 1.0 | No | Fetched | Puppet era |
| S9 | DORA FAQ | dora.dev | primary 1.0 | No | Fetched | Same |
| S10 | Forsgren, Google Cloud blog 2019 report (2019-08-23) | cloud.google.com | primary 1.0 | No | Fetched | Cloud finding = sponsor interest |
| S11 | DeBellis & Peters, Google Cloud blog 2022 report (2022-09-29) | cloud.google.com | primary 1.0 | No | Fetched | Same |
| S12 | Keunwoo Lee, review of *Accelerate* (2022-06-07) | keunwoo.com | **not on trusted list** (treated 0.5) | Yes | Fetched | Single critic; author has a public reply from Humble (not read) |
| S13 | DORA research overview | dora.dev | primary 1.0 | No | Fetched | |
| S14 | DORA 2022 research page | dora.dev | primary 1.0 | No | Fetched | |
| S15 | Forsgren, "The Key to High Performance" eBook (2017) | itrevolution.com | primary 1.0 | No | Fetched | |
| S16 | Tacho, 2024 DORA report summary (2024-10-29) | getdx.com | vendor 0.6 | Yes | Fetched | Sells developer-productivity analytics |
| S17 | Sallin et al., XP 2021, LNBIP 419 (Springer) | springer.com venue; **fetched host irf.fhnw.ch is not on the trusted list** (university repository) | academic 1.0 (venue) | Yes | Abstract fetched | |
| S18 | Khomh et al., MSR 2012 (IEEE) | ieee.org venue; **host swat.polymtl.ca is not on the trusted list** (author's university page) | academic 1.0 (venue) | Yes | **Abstract only**, via search; PDF not fetched | Single product (Firefox) |
| S19 | Fowler, Is High Quality Software Worth the Cost? (2019) | martinfowler.com | practitioner 0.8 | Partly (cites DORA for the trade-off) | Fetched | |
| S20 | DORA 2024 report landing page | dora.dev | primary 1.0 | No | Fetched | |
| S21 | Harvey & DeBellis, Google Cloud blog 2025 report (2025-09-23) | cloud.google.com | primary 1.0 | No | Fetched | AI vendor sponsoring AI research |
| S22 | Saunders, InfoQ news (2025-09-29) | infoq.com | practitioner 0.8 | Yes (reporting) | Fetched | Reports DORA claims |
| S23 | continuousdelivery.com principles | continuousdelivery.com | practitioner 0.8 | No (Humble) | Fetched | |
| S24 | Fowler, FrequencyReducesDifficulty (2011) | martinfowler.com | practitioner 0.8 | Yes | Fetched | |
| S25 | DORA 2024 survey questions | dora.dev | primary 1.0 | No | Fetched | |
| S26 | DORA capabilities catalogue | dora.dev | primary 1.0 | No | Fetched | |
| S27 | DORA 2025 measurement frameworks | dora.dev | primary 1.0 | No | Fetched | |
| S28 | Finster, "How to Misuse & Abuse DORA Metrics" (May 2022) | itrevolution.com | primary-domain 1.0 | Yes (independent author) | Summary page fetched | |
| S29 | Forsgren, Storey, Maddila, Zimmermann, Houck, Butler, SPACE, ACM Queue 19(1), 2021 | acm.org venue; **fetched host microsoft.com is not on the trusted list** (co-authors' employer page) | academic 1.0 (venue) | Partly (Forsgren co-author) | Abstract fetched; Queue 403 | |
| S30 | *Accelerate* excerpt "Focus on capabilities, not maturity" | techtarget.com | **not on trusted list** (treated 0.5) | No (book text) | Fetched | Publisher-licensed excerpt |
| S31 | Manheim & Garrabrant, "Categorizing Variants of Goodhart's Law" (2018/2019) | arxiv.org | academic 1.0 | Yes | Fetched | |
| S32 | DORA 2023 report abstract | research.google (**not literally on the trusted list**; Google's own research publications site, so the same programme as cloud.google.com) | primary 1.0 | No | Fetched | |
| S33 | DORA 2025 sponsors | dora.dev (web page https://dora.dev/research/2025/sponsors/, **not the local PDF**; the sponsor list does not appear in the extracted 2025 PDF text) | primary 1.0 | No | Fetched from web | Lists vendor sponsors |
| S34 | Forsgren, Humble, Kim, *Accelerate* (2018) | local epub (IT Revolution) | primary 1.0 | No | **Read in full where cited** (ch. 1-3, 12-15, App. A-C) | Authors' own research; sample drawn partly from Puppet marketing lists (ch. 15) |
| S35 | DORA, *Accelerate State of DevOps Report 2024* v. 2024.3 | local PDF (dora.dev) | primary 1.0 | No | **Read; printed page cited** | Google Cloud |
| S36 | DORA, *State of AI-assisted Software Development 2025* v. 2025.2 | local PDF (dora.dev) | primary 1.0 | No | **Read; printed page cited** | Google Cloud; vendor sponsors [S33] |

Post-verification notes: S16 (Tacho) and S30 (TechTarget) are now redundant for every claim they supported. Each claim is re-cited to S35 or S34. S30 is retained only as a pointer. S12 (Lee) is now corroborated by the book on every factual point used (snowball sampling, p < 0.10, "inferential predictive", drives/impacts wording).

Reputation: primary-research domains 22 of 36 (61%): 21 DORA-programme sources (S1-3, S5, S8-11, S13-15, S20-21, S25-27, S32-36) plus S28 (Finster, on itrevolution.com but an independent author). Academic 4 (11%), practitioner 7 (19%), vendor 1 (3%), unlisted 2 (6%, flagged, now redundant). **Average ≈ 0.92.** **Source-bias warning:** the reputation average is high *because* most sources are DORA's own. For independence, those 21 count as one source. Independent of DORA: S6, S7 (2018-2022 blips only; 2025-26 blips are excluded from High-confidence counts because of the 2025 sponsorship), S12, S16, S17, S18, S22, S24, S28, S31 (plus S19, S29 partly). Excluded or not-trusted sources seen but **not cited as evidence**: Goodreads highlights, thenewstack.io, cusy.io, redmonk.com, octopus.com, techtarget news, Wikipedia, hackernoon, scrums.com.

## Knowledge Gaps

### Gap 1: Independent replication of "delivery performance predicts organizational performance"
**Issue**: No peer-reviewed, non-DORA study reproducing the link was found. **Attempted**: arXiv/Springer searches, critiques search. **Page impact**: keep the caveat on the page. This is a DORA finding with weak independent corroboration. **Recommendation**: Present as DORA's finding with "predicts / is associated with" language. Search Google Scholar for "software delivery performance" AND "organizational performance" replication.

### Gap 2: Independent evidence on the Throughput/Instability non-trade-off across organizations
**Issue**: Only Khomh et al. was found (one product, release cadence rather than DORA metrics, abstract only). **Attempted**: arXiv/Springer and practitioner searches, plus one more academic search in review round 1 (repository telemetry, Deployment Frequency against Change Fail Rate), which returned only vendor material. **Page impact**: keep the caveat on the page. This is a DORA finding with weak independent corroboration. **Recommendation**: Look for telemetry-based studies (e.g. ICSSP 2024 Rüegger et al., vuw.ac.nz, whose PDF could not be parsed) and vendor datasets, flagging their interest.

### Gap 3: Story points and velocity as productivity measures (independent source)
**Issue**: The primary is now the book (ch. 2 [S34]), but there is still no independent trusted source. **Recommendation**: Add an independent agile source if the page leans on velocity.

### Gap 8: Independent evidence that the DORA capabilities drive delivery performance
**Issue**: Finding 2.4 is DORA-only (regressions on DORA's self-reported survey). No non-DORA source was sought or found. **Recommendation**: Attribute it on the page ("DORA's research identifies..."). Look for independent studies on specific capabilities (e.g. trunk-based development, test automation) if the page makes capability-level claims.

### Gap 9: 2022 report not read
**Issue**: The 2022 exceptions (no elite cluster, "Slowing") come from the Google Cloud announcement blog [S11] only. **Recommendation**: Read the 2022 report before quoting its cluster shares on the page.

### Gap 4: CLOSED. Why Failed Deployment Recovery Time is grouped with Throughput
Answered by the 2024 report p. 12 [S35]: Throughput "measures the speed of making updates of any kind, normal changes and changes in response to a failure."

### Gap 5: CLOSED. 2025 profiles
All seven names and shares verified (pp. 16-18 [S36]). Reason for the change: metrics show what, not why (p. 14 [S36]).

### Gap 6: CLOSED. Local primaries verified
- 2024 AI figures: correct as −1.5% Throughput and "7.2% reduction" in "delivery stability" (i.e. higher Instability) per 25% AI adoption (pp. 39-40 [S35]).
- 2024 cluster shares: correct at 19/22/35/25 (p. 13 [S35]).
- p. 14 citation (S16): correct. p. 14 holds the "Throughput or stability?" discussion; the cluster table itself is on p. 13.
- p. 37 citation (S16): correct for the AI/documentation chart. Figure 9 shows 7.5% documentation quality per 25% AI adoption.
- *Accelerate* method, Westrum, no-trade-off, org-performance and maturity claims: all verified by chapter.
Remaining nuance: the 2023 report (cluster shares 2023, "31%" High and "17%" Low cited by S16 as prior year) was not checked; no local copy.

### Gap 7: Humble's reply to Lee (2022-07-08)
**Issue**: medium.com returned 403. It is no longer needed, because the book (ch. 12) and the 2024 report (p. 110) state the non-causal design directly. Low priority.

## Conflicting Information

### Conflict 1: Is Change Fail Rate part of the same construct as speed?
**Position A**: DORA's public message: speed and stability "are not tradeoffs"; the metrics are correlated for most teams [S1]; "they move in tandem" (*Accelerate* App. B [S34]). **Position B**: The same programme: the four measures "don't pass all of the statistical tests" as one construct (*Accelerate* ch. 3 [S34]); "statistical tests and methods prevent us from combining all four into one factor" (2024 p. 11 [S35]). In 2016 Medium was worse than Low on Change Fail Rate [S34]; in 2024 Medium beat High on it (p. 13 [S35]). **Assessment**: Not a contradiction. They are correlated but distinct. The page should say "tend to move together" or "do not trade off on average", not "are the same thing".

### Conflict 2: Are DORA's methods and questions open?
**Position A**: Lee (2022): the authors "have never publicly released either their full questions" or data [S12]. **Position B**: DORA FAQ (current): "We make our research methods and survey questions available under a Creative Commons license", but not raw data [S9]. 2024 questions are published [S25]. **Assessment**: Both can be true at different times. Lee was writing about the *Accelerate* era, while recent years publish questions. Raw data remains unavailable, so independent re-analysis is still impossible.

### Conflict 3: Timing of the Google acquisition
**Position A**: 2018. **Position B**: 2019 (getdx.com, in search results only). **Assessment**: Unresolved. Avoid the date. Say "since 2018 DORA has run the research with Google Cloud" (2018 report was with Google Cloud [S5]).

### Conflict 4: "Twice as likely" organizational-performance figure
**Position A**: *Accelerate* ch. 2: "Analysis over several years shows that high-performing organizations were consistently *twice as likely* to exceed these goals [profitability, market share, productivity] as low performers" [S34]; also the 2014 page [S8]. **Position B**: Secondary sources cite 1.53x (elite, 2018) and other multiples. **Assessment**: "Twice as likely" is safe if attributed to *Accelerate* (2014-2017 data, high versus low performers, self-rated organizational performance). Other multiples belong to other years.

### Conflict 5: Respondent counts
2024: "nearly 3,000" that year, "roughly 39,000" cumulative (p. 91 [S35]). 2025: "nearly 5,000" (p. 3 [S36]). The 2023 figure was not verified; secondary "36,000" is a cumulative count. Always give the year.

### Conflict 6: *Accelerate* recommended targets; current DORA guidance warns against them
**Position A**: *Accelerate* ch. 2 (2018): "Use our measures for lead time, deployment frequency, time to restore service, and change fail rate, and ask your teams to set targets for these measures." It also says "We can compare and benchmark teams against the larger organizations they work in and against the wider industry." In the same passage it warns that in pathological cultures "measurement is used as a form of control" [S34]. **Position B**: dora.dev today: "Setting metrics as a goal" is the first pitfall, along with "Competing" and "Making disparate comparisons" [S1]; 2024: "Improving should be more important to a team than reaching a particular performance level" (p. 14 [S35]). **Assessment**: The guidance has evolved. Team-owned improvement targets inside a learning culture (2018) are not the same as top-down mandates such as "every application must deploy multiple times per day" (current pitfall). Present it as the programme learning from misuse, and do not quote the 2018 line as current advice.

### Conflict 7: "Stability" versus "Instability" for the second factor
2024 report: "software delivery stability" factor (pp. 11-12 [S35]); 2025 report and dora.dev: "Instability" [S36 p. 13], [S1]. Same metrics, inverse framing. Use the glossary term (Instability). Quotes from 2024 keep "stability".

## Writer's brief

### Key claims ranked by confidence
**High (quote freely, credit source):**
1. The five definitions and the Throughput/Instability grouping, verbatim from dora.dev [S1].
2. Output measures (lines of code, utilization, velocity) fail because they measure output not outcomes and local/individual not global/team (*Accelerate* ch. 2 [S34]; [S6]).
3. DORA's pitfalls list (targets, one metric, disparate comparisons, competing, siloed ownership, measurement over improvement) [S1], backed by [S7], [S28], [S29], [S31], [S35] p. 14.
4. The metrics changed over time: MTTR became Failed Deployment Recovery Time in 2023, rework rate was added in 2024 (as a test of whether Change Fail Rate is a proxy for rework), and the metrics were regrouped into two factors. Failed Deployment Recovery Time sits under Throughput because Throughput "measures the speed of making updates of any kind, normal changes and changes in response to a failure" ([S2]; [S35] pp. 11-12).
5. Clusters emerge from the data, are recomputed yearly, and are not a maturity model ([S34] ch. 1-2; [S35] pp. 13-15).
6. The research is a self-reported, snowball-sampled, DevOps-familiar survey analysed with psychometrics, clustering and regression. It is explicitly not causal ([S34] ch. 12-15; [S35] p. 110). It ran first with Puppet and then at Google Cloud.
7. 2024 numbers (as reported by DORA): per 25% increase in AI adoption, −1.5% Throughput and a 7.2% rise in Instability, which the 2024 report words as "an estimated 7.2% reduction" in "delivery stability" (pp. 39-40 [S35]). Clusters 19/22/35/25 (p. 13 [S35]). 2025 profiles: seven, with shares (pp. 16-18 [S36]).

**Medium: DORA findings with weak independent corroboration. Keep this caveat on the page.**
8. **DORA finding, weak independent corroboration:** Throughput and Instability do not trade off on average; the best teams are fast and stable ([S34] ch. 2; [S35] p. 10; [S1]). Outside DORA there is only one abstract-level case study [S18] and practitioner mechanism arguments [S23], [S24], [S19] (Gap 2). They are separate factors and increasingly diverge ([S35] pp. 11, 39; [S36] p. 4). Suggested page wording: "DORA's surveys have consistently found... Independent studies are scarce."
9. **DORA finding, weak independent corroboration:** Software Delivery Performance predicts organizational performance ("twice as likely", self-rated) (*Accelerate* ch. 2 [S34]; [S8], [S10]). Correlational, with no independent replication found (Gap 1). Suggested page wording: "DORA reports that... (survey-based, correlational)."
10. Small batches and fast feedback are the main explanation ([S34] ch. 2; [S23], [S24]). DORA's 2024 hypothesis that AI grew batch size is consistent with this, but batch size was not measured ([S35] p. 40).
11. Capabilities drive performance: DORA only (Gap 8). Attribute it.
12. 2025: "AI's primary role in software development is that of an amplifier" (p. 3 [S36]). This is DORA's interpretation.

### Suggested narrative arc
1. **Why measure, and why it is hard**: Open with "the inventory is invisible" ([S34] ch. 2) and Fowler's "we can't measure output" [S6]. Show the three failed measures with one sharp line each (10-line versus 1,000-line solution; velocity "designed to be used as a capacity planning tool"; "as utilization approaches 100%, lead times approach infinity") [S34]. Land on the two characteristics: a global outcome so "teams aren't pitted against each other", and "outcomes not output" [S34], with the "wall of confusion" as the picture.
2. **Where the answer came from**: The State of DevOps programme (2014 onwards, Puppet, then DORA at Google Cloud). In plain words: "A latent construct is a way of measuring something that can't be measured directly" [S34 ch. 13]; the clustering algorithm "doesn't know what counts as a 'good' or 'bad' response" [S34 ch. 2]. The headline finding ("twice as likely"). Then an honest limits paragraph in the authors' own words: the sample misses "a cohort that are likely performing even worse than our low performers" [S34 ch. 15]; "we didn't do longitudinal studies or a proper experiment" [S35 p. 110].
3. **The surprise: fast and stable**: State the finding in the book's words ("Astonishingly...") [S34], explain small batches and "if it hurts, do it more often" [S24], then show it is a tendency, not a law: 2016 medium-vs-low anomaly, 2022 "Slowing", 2024's "We made a decision to call the faster teams 'high performers'" [S35 p. 14], and 2025's AI divergence [S36 p. 4].
4. **The framework today**: Five metrics verbatim, two groups, a short history table (MTTR → Failed Deployment Recovery Time; Deployment Rework Rate added in 2024). Place them in capabilities → performance → outcomes, and mention 2025's seven profiles and "AI amplifies".
5. **How it goes wrong**: Use DORA's own pitfall headings as the backbone, adding Goodhart, team comparison ("improve your team's performance over time, not ... compete"), individuals, maturity-model thinking, one-metric focus, and dashboards-first (Thoughtworks: check in at retrospectives before building dashboards). Close with DORA's loop: baseline, find the bottleneck, improve, repeat [S1].

### Quotes ready for use (exact, with source)
- "Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is invisible." [S34 ch. 2]
- "the reason we can't measure productivity is because we can't measure output." [S6]
- "velocity is a relative and team-dependent measure, not an absolute one." [S34 ch. 2]
- "Queue theory in math tells us that as utilization approaches 100%, lead times approach infinity" [S34 ch. 2]
- "When you focus on global outcomes, productivity follows." [S4]
- "Astonishingly, these results demonstrate that there is no tradeoff between improving performance and achieving higher levels of stability and quality." [S34 ch. 2]
- "As Deming said, 'whenever there is fear, you get the wrong numbers'" [S34 ch. 2, quoting Humble et al. 2014]
- "we cannot stress enough that maturity models are not the appropriate tool to use or mindset to have." [S34 ch. 1]
- "The best teams are those that achieve elite improvement, not necessarily elite performance." [S35 p. 14]
- "Correlation does not imply causation, but it does imply how you think about causation." [S35 p. 110]. Re-verified: the sentence wraps across three lines of the extracted text (Methodology, "Causality", PDF page 110). The 2025 report has a different variant: "Correlation does not imply causation, but our assumptions about causation do impact the correlations we find." [S36 p. 131]. Do not mix the two.
- "AI's primary role in software development is that of an amplifier. It magnifies the strengths of high-performing organizations and the dysfunctions of struggling ones." [S36 p. 3]
- "they are ultimately outcomes. They tell you what is happening, but they don't explain why." [S36 p. 14]
- "DORA's research has repeatedly demonstrated that speed and stability are not tradeoffs." [S1]
- "if it hurts, do it more often." [S24]
- "The goal is to improve your team's performance over time, not to compete against other teams or organizations." [S1]
- "AI doesn't fix a team; it amplifies what's already there." [S21]
- "Simple software delivery metrics alone aren't sufficient. They tell you what is happening but not why it's happening." [S21]
- "Stability metrics only make sense if they include data about real incidents that degrade service for the users." [S7]
- "We have never dictated the number of clusters; they are emergent from the patterns in the data." [S9]

### Claims to AVOID or hedge
- **Avoid** "DORA proved that X causes Y". Use "predicts" or "is associated with". The authors say causal analysis was "not included in our research" ([S34] ch. 12; [S35] p. 110).
- **Avoid** elite-versus-low multiples unless tied to a year: 2017 is 200x / 2,555x [S15]; 2024 is 127x / 182x / 8x / 2293x ([S35] p. 15).
- **Avoid** quoting *Accelerate*'s "ask your teams to set targets" as current advice (Conflict 6).
- **Avoid** a Google acquisition date (Conflict 3).
- **State with care**: the 2024 AI figures are per 25% increase in AI adoption, estimates with 89% uncertainty intervals, and associations ([S35] pp. 39-40). The 2025 report re-expresses the stability figure as a 7.2% *increase in instability* (p. 35 [S36]). Same finding.
- **Hedge** "Throughput and Instability move together": say "tend to", "on average", and mention the exceptions. Remember that Instability goes *down* as performance improves.
- **2025 profiles**: names are "an interpretation of the data" (p. 16 [S36]). Present them as illustrative, not as categories to assign teams to.
- **Use glossary terms**: Change Fail Rate (not "change failure rate"), Failed Deployment Recovery Time (not MTTR), Deployment Rework Rate (not "rework rate"), Instability (not "stability" except inside quotes). Inside quotes keep the source's words and add the glossary term in brackets.
- **Flag sponsorship once, factually**: Puppet then Google Cloud; the 2025 report also had vendor sponsors. The list of names is from the dora.dev sponsors web page [S33], not from the report PDF. If you name them, cite that page. Do not imply the findings are invalid because of this.
- **Keep the independence caveat on the page** for items 8 and 9 above. Do not present them as settled science.

## Full Citations

[S1] DORA. "DORA's software delivery performance metrics". dora.dev. https://dora.dev/guides/dora-metrics/. Accessed 2026-10-17.
[S2] Harvey, N. "A history of DORA's software delivery metrics". dora.dev. 2026-01-02. https://dora.dev/guides/dora-metrics/history/. Accessed 2026-10-17.
[S3] Forsgren, N., Kim, G., Humble, J. "Measure Software Delivery Performance with Four Key Metrics". IT Revolution. 2021-02-25. https://itrevolution.com/measure-software-delivery-performance-four-key-metrics/. Accessed 2026-10-17.
[S4] Forsgren, N. "Measuring Tech Performance: You're Probably Doing It Wrong". InfoQ. 2018-07-22. https://www.infoq.com/articles/measuring-tech-performance-wrong. Accessed 2026-10-17.
[S5] Meckfessel, M. Google Cloud blog post announcing the 2018 Accelerate State of DevOps Report. 2018-08-29. https://cloud.google.com/blog/products/devops-sre/new-research-what-sets-top-performing-devops-teams-apart. Accessed 2026-10-17 (search snippet only).
[S6] Fowler, M. "CannotMeasureProductivity". martinfowler.com. 2003-08-29. https://martinfowler.com/bliki/CannotMeasureProductivity.html. Accessed 2026-10-17.
[S7] Thoughtworks. "DORA metrics" (and earlier "Four key metrics") blips, Technology Radar, Nov 2018 to Apr 2026. https://www.thoughtworks.com/radar/techniques/dora-metrics. Accessed 2026-10-17.
[S8] DORA. "DORA Research: 2014". dora.dev. https://dora.dev/research/2014/. Accessed 2026-10-17.
[S9] DORA. "FAQ". dora.dev. https://dora.dev/faq/. Accessed 2026-10-17.
[S10] Forsgren, N. "The 2019 Accelerate State of DevOps: Elite performance, productivity, and scaling". Google Cloud blog. 2019-08-23. https://cloud.google.com/blog/products/devops-sre/the-2019-accelerate-state-of-devops-elite-performance-productivity-and-scaling. Accessed 2026-10-17.
[S11] DeBellis, D., Peters, C. "Announcing the 2022 Accelerate State of DevOps Report: A deep dive into security". Google Cloud blog. 2022-09-29. https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/. Accessed 2026-10-17.
[S12] Lee, K. "A review of *Accelerate: The Science of Lean Software and DevOps*". 2022-06-07. https://keunwoo.com/notes/accelerate-devops/. Accessed 2026-10-17. [Not on trusted list; flagged]
[S13] DORA. "Research". dora.dev. https://dora.dev/research/. Accessed 2026-10-17.
[S14] DORA. "DORA Research: 2022". dora.dev. https://dora.dev/research/2022/. Accessed 2026-10-17.
[S15] Forsgren, N. "The Key to High Performance" (eBook based on DevOps Enterprise Summit 2017 talk). IT Revolution. https://reader.itrevolution.com/library/the-key-to-high-performance. Accessed 2026-10-17.
[S16] Tacho, L. "2024 DORA report summary". DX (getdx.com). 2024-10-29. https://getdx.com/blog/2024-dora-report-summary-laura-tacho/. Accessed 2026-10-17. [Vendor]
[S17] Sallin, M., Kropp, M., Anslow, C., Quilty, J. W., Meier, A. "Measuring Software Delivery Performance Using the Four Key Metrics of DevOps". XP 2021, LNBIP 419, pp. 103-119. Springer. doi:10.1007/978-3-030-78098-2_7. https://irf.fhnw.ch/entities/publication/f1027f63-e9f7-4291-bcac-584e6647e891/full. Accessed 2026-10-17.
[S18] Khomh, F., Dhaliwal, T., Zou, Y., Adams, B. "Do Faster Releases Improve Software Quality? An Empirical Case Study of Mozilla Firefox". MSR 2012 (IEEE). https://swat.polymtl.ca/~foutsekh/docs/Khomh-MSR-2012.pdf. Accessed 2026-10-17 (abstract via search).
[S19] Fowler, M. "Is High Quality Software Worth the Cost?". martinfowler.com. 2019-05-29. https://martinfowler.com/articles/is-quality-worth-cost.html. Accessed 2026-10-17.
[S20] DORA. "DORA Report 2024". dora.dev. https://dora.dev/research/2024/dora-report/. Accessed 2026-10-17.
[S21] Harvey, N., DeBellis, D. "Announcing the 2025 DORA Report". Google Cloud blog. 2025-09-23. https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report. Accessed 2026-10-17.
[S22] Saunders, M. "DORA State of AI-assisted Software Development 2025" (news). InfoQ. 2025-09-29. https://www.infoq.com/news/2025/09/dora-state-of-ai-in-dev-2025. Accessed 2026-10-17.
[S23] Humble, J. "Principles". continuousdelivery.com. https://continuousdelivery.com/principles/. Accessed 2026-10-17.
[S24] Fowler, M. "FrequencyReducesDifficulty". martinfowler.com. 2011-07-28. https://martinfowler.com/bliki/FrequencyReducesDifficulty.html. Accessed 2026-10-17.
[S25] DORA. "2024 survey questions". dora.dev. https://dora.dev/research/2024/questions/. Accessed 2026-10-17.
[S26] DORA. "Capabilities". dora.dev. https://dora.dev/capabilities/. Accessed 2026-10-17.
[S27] DORA. "Measurement frameworks" (2025). dora.dev. https://dora.dev/research/2025/measurement-frameworks/. Accessed 2026-10-17.
[S28] Finster, B. "How to Misuse & Abuse DORA Metrics". IT Revolution guidance paper. May 2022. https://reader.itrevolution.com/library/how-to-misuse-abuse-dora-metrics. Accessed 2026-10-17.
[S29] Forsgren, N., Storey, M.-A., Maddila, C., Zimmermann, T., Houck, B., Butler, J. "The SPACE of Developer Productivity". ACM Queue 19(1), 2021, pp. 20-48. https://queue.acm.org/detail.cfm?id=3454124 (abstract read via https://www.microsoft.com/en-us/research/?p=733804). Accessed 2026-10-17.
[S30] Forsgren, N., Humble, J., Kim, G. *Accelerate* excerpt "Focus on capabilities, not maturity". TechTarget. https://www.techtarget.com/it-infrastructure/opinion/DevOps-Research-and-Assessment-team-dispels-maturity-model-myths. Accessed 2026-10-17. [Not on trusted list; publisher excerpt of the book, flagged]
[S31] Manheim, D., Garrabrant, S. "Categorizing Variants of Goodhart's Law". arXiv:1803.04585. 2018 (rev. 2019). https://arxiv.org/abs/1803.04585. Accessed 2026-10-17.
[S32] DORA / Google. "Accelerate State of DevOps 2023" (abstract). research.google. https://research.google/pubs/accelerate-state-of-devops-2023/. Accessed 2026-10-17.
[S33] DORA. "2025 sponsors". dora.dev. https://dora.dev/research/2025/sponsors/. Accessed 2026-10-17.

[S34] Forsgren, N., Humble, J., Kim, G. *Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations*. IT Revolution, 2018. Local copy `harness/accelerate-the-science-of-devops.epub`. Cited by chapter/appendix (epub has no stable page numbers).
[S35] DORA (Google Cloud). *Accelerate State of DevOps Report 2024*, v. 2024.3. Local copy `harness/2024-dora-accelerate-state-of-devops-report.pdf` (also https://dora.dev/research/2024/dora-report/). Cited by printed page.
[S36] DORA (Google Cloud). *State of AI-assisted Software Development 2025*, v. 2025.2. Local copy `harness/2025_state_of_ai_assisted_software_development.pdf` (also https://dora.dev/research/2025/dora-report/). Cited by printed page.

## Research Metadata
Examined: about 50 web pages and search result sets plus the three local primaries | Cited: 36 | DORA-programme sources (count as one for independence): 21, or 22 on primary-research domains including Finster | Independent sources: 10 full plus 2 partial | Confidence by section (after review 1): §1 Medium-High, §2 High (method) / Medium (org-performance link: DORA finding, weak independent corroboration), §3 Medium (no-trade-off: DORA finding, weak independent corroboration) / High (exceptions, except 2022 Medium), §4 High, §5 High (5.6 Medium-High) | Initial tool failures (resolved by orchestrator text extraction): epub unzip, PDF render, web PDFs over 10 MB. Still unresolved: HTTP 403 (queue.acm.org, medium.com), unparsable PDFs (zhaw.ch, vuw.ac.nz, usenix.org, uncw.edu) | Output: docs/research/measuring-software-delivery-performance-for-explanation-doc.md

## Review 1 (Scholar)

```yaml
review_id: "research_rev_20261017_measuring_sdp"
reviewer: "nw-researcher-reviewer (Scholar)"
date: "2026-10-17"
verdict: "NEEDS_REVISION"
iteration: 1
max_iterations: 2
spot_checks_passed: ["inventory is invisible", "twice as likely", "2016 medium worse than low on CFR", "causal analysis not included", "only lead time, release frequency...", "p < 0.10", "longitudinal studies (2024 p.110)", "127x / 2293x", "7.2%", "AI amplifier", "2025 profile names", "marketing databases", "nearly 3,000 / roughly 39,000", "2024 clusters 19%/35%"]
spot_checks_failed:
  - {claim: "Correlation does not imply causation...", note: "cited 2024 p.110; found only in dora-2025.txt l.9471"}
  - {claim: "Khomh/Firefox quote", note: "UNVERIFIED, abstract only; cited as S19 instead of S18"}
  - {claim: "2025 sponsor list (Thoughtworks platinum, Swarmia, Jellyfish, Atlassian)", note: "not found in local 2025 PDF"}
issues:
  - {severity: critical, issue: "61-64% sources DORA-programme", fix: "Brief labels predictive and trade-off claims 'DORA finding, weak independent corroboration'; keep Gaps 1-2 visible for page"}
  - {severity: high, issue: "Correlation quote misattributed", fix: "Re-cite to 2025 report printed page or drop; check 'causal thinking is how we understand the world' too"}
  - {severity: high, issue: "Khomh quote", fix: "Cite S18, mark abstract-based or verify"}
  - {severity: high, issue: "Exec summary overclaims 'every report since 2015' and CFR 'never fit'", fix: "'on average, with documented exceptions'; 'did not fit four-metric construct in Accelerate ch.3'"}
  - {severity: high, issue: "2022 exceptions rated High via blog S11", fix: "Downgrade to Medium or read 2022 report"}
  - {severity: high, issue: "Sponsor list unverified", fix: "Verify on dora.dev or say only 'vendor sponsors'"}
  - {severity: medium, issue: "Finding 1.1 High with two sources", fix: "Medium-High"}
  - {severity: medium, issue: "Finding 2.4 DORA-only no gap", fix: "State gap"}
  - {severity: medium, issue: "S7 counted independent for 2025-26 claims", fix: "Exclude from High count"}
  - {severity: medium, issue: "Exec summary uncited", fix: "Add inline [S#]"}
  - {severity: medium, issue: "Source count 23 vs 22", fix: "Correct"}
  - {severity: medium, issue: "Out-of-list domains unflagged", fix: "Flag S32 research.google, S29 microsoft.com, S17 irf.fhnw.ch, S18 swat.polymtl.ca"}
  - {severity: medium, issue: "'stability' used for Instability in brief item 7", fix: "Use Instability or quote"}
  - {severity: medium, issue: "S7 Radar quotes unverifiable locally", fix: "Mark Medium"}
quality_scores: {source_bias: 0.45, evidence_quality: 0.70, replicability: 0.80, completeness: 0.75}
```

## Revision 1 response

1. **Critical, source bias**: I did not add weak sources. Changes:
   - A source-bias caveat box now opens the Executive Summary.
   - The Writer's brief puts the no-trade-off claim (item 8) and the predictive claim (item 9) in a "DORA finding, weak independent corroboration" tier, with suggested page wording, and adds an instruction to keep the caveat on the page.
   - Gaps 1-2 now have a "Page impact" line.
   - One more academic search (repository telemetry, Deployment Frequency against Change Fail Rate) found nothing trusted, so nothing was added.
2. **High, correlation quote**: The quote is on 2024 p. 110 and the citation stands. The reviewer's grep missed it because the sentence wraps over lines 4895-4897 of dora-2024.txt, under the PAGE 110 marker. "causal thinking is how we understand the world" is also verified (lines 4891-4892). The 2025 report (p. 131) has a different variant, now noted next to the quote so the two are not mixed.
3. **High, Khomh quote**: The quote is attributed to [S18] in its own bullet and marked "[Abstract-based]". Finding 3.1 is lowered to Medium.
4. **High, Executive Summary overclaims**: "every report since 2015" is replaced by "on average... consistently, with documented exceptions". "Never fit" is replaced by "did not fit the four-metric construct in *Accelerate* [S34 ch. 3]".
5. **High, 2022 exceptions**: Marked "blog only; report not read" in the table and in Finding 3.4 item 3 (Medium). The Finding 3.4 confidence is split by item. New Gap 9.
6. **High, sponsor list**: The list came from the dora.dev web page [S33], fetched live, not from the PDF. The Source Analysis now says so. The brief now says "vendor sponsors" and asks the writer to cite the web page if naming them.
7. **Medium, Finding 1.1**: Downgraded to Medium-High.
8. **Medium, Finding 2.4**: Gap stated in the finding. New Gap 8.
9. **Medium, S7 counted independent for 2025-26 claims**: Excluded from High counts in Findings 1.2, 1.3, 5.2 and 5.6. The Source Analysis notes that only the 2018-2022 blips count as independent.
10. **Medium, Executive Summary uncited**: Inline [S#] citations added throughout.
11. **Medium, source count**: Corrected to 22 of 36 on primary-research domains (21 DORA programme plus Finster), 61%. The Research Metadata line is updated.
12. **Medium, out-of-list domains**: S17, S18, S29 and S32 are flagged in the Source Analysis.
13. **Medium, "stability" in brief item 7**: Reworded to "higher Instability", with the 2024 "stability" wording kept only inside the quote. The Executive Summary and Gap 6 are aligned the same way.
14. **Medium, S7 Radar quotes**: Marked Medium wherever used (Findings 1.2, 1.3, 5.2, 5.6).

## Review 2 (Scholar)

```yaml
review_id: "research_rev_20261017_measuring_sdp_r2"
reviewer: "nw-researcher-reviewer (Scholar)"
date: "2026-10-17"
verdict: "APPROVED"
iteration: 2
max_iterations: 2
corrections:
  - {claim: "Correlation does not imply causation (2024 p.110)", result: PASS, note: "line-wrapped at dora-2024.txt l.4895-4897; review 1 FAIL was a false positive"}
issues_resolved: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
issues_identified:
  source_bias:
    - {severity: medium, issue: "Caveat box said 22 of 36 (61%) DORA-programme; Finster is independent, so 21 of 36 (58%)", recommendation: "Fix caveat box", status: "fixed by orchestrator"}
  evidence_quality:
    - {severity: medium, issue: "2025 p.131 citation for variant correlation wording not re-checked", recommendation: "Confirm page", status: "confirmed by orchestrator: PDF page 131"}
quality_scores: {source_bias: 0.70, evidence_quality: 0.85, replicability: 0.85, completeness: 0.85}
approval_status: "approved"
blocking_issues: []
```
