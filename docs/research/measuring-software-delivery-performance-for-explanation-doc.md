# Research: Measuring Software Delivery Performance (for an Explanation page)

**Date**: 2026-10-17 (revision 4) | **Researcher**: nw-researcher (Nova) | **Confidence**: Medium overall (see per-section ratings) | **Sources**: 29 cited | **Supersedes**: `measuring-software-delivery-performance-comprehensive-research.md` (removed; see git history)

**Source-bias metric**: 21 of 29 cited sources (72%) are not independent of DORA. 16 are DORA programme publications (B1, B1-F, D1, D2, D3, D4, D6, D8, D9, G1, G2, G3, G4, P1, R24, R25). 5 are DORA-authored or co-authored by Nicole Forsgren (A1, A2, I1, I3, I4). 8 (28%) are independent (A5, A6, A7, I2, F1, T1, V1, V2). Of those 8, two are vendors (V1, V2) and one is an unverified search extract (A6) that supports nothing. Under the trusted-source rules the programme counts as ONE source. A claim reaches High only with support outside both the programme and DORA-authored work.

## Executive Summary

Software delivery is hard to measure because its inventory is invisible, work breakdown is arbitrary and design overlaps with delivery (*Accelerate*, Ch 2). Output measures such as lines of code, velocity (historical term) and utilization fail: they reward local busywork, they cannot be compared across teams, and they get gamed. *Accelerate* (Forsgren, Humble, Kim, 2018) measured a **global outcome** instead, one that development and operations must improve together. The book draws on four years of Puppet-run State of DevOps surveys (2014-2017; over 23,000 responses from over 2,000 organisations). Its methods are Likert-type psychometric constructs, cluster analysis that categorises "without any bias toward 'good' or 'bad'", and theory-driven inferential prediction. High performers were "twice as likely" to exceed organisational goals (*Accelerate* data, 2014-2017). The authors state that they did no causal analysis, and that their data is cross-sectional, self-reported and snowball-sampled. Martin Fowler's foreword adds his own caveats: survey data captures subjective perceptions, the sample may not represent the industry, confirmation bias is a risk, and the scope is commit-to-production only. The foreword is printed in the book, so it is not an independent publication.

The headline finding is that Throughput and Instability are not a trade-off. High performers do better on all measures, and DORA in 2026 still says "speed and stability are not tradeoffs". **This is a programme finding that has not been independently replicated.** It is endorsed in Fowler's foreword, which is printed in the programme's own book. Thoughtworks lists the metrics as a technique on its Technology Radar. Neither tests the trade-off claim. No peer-reviewed replication outside DORA was found. It is also a population-level, correlational finding with documented exceptions: in 2016 medium performers had a worse change fail rate than low performers; in 2022 no Elite cluster appeared; in 2024 the Medium cluster had a lower change fail rate (10%) than the High cluster (20%), and DORA named "the slower but more stable teams 'medium performers'", while still finding throughput and stability "correlated" within all four clusters (DORA 2024 report, pp. 13-14); in 2024 AI adoption went with lower Throughput and a "reduction" in delivery stability (2024 report, p. 40); in 2025 AI adoption "now improves software delivery throughput" but "still increases delivery instability" (DORA 2025 report, p. 4). The authors propose small batches, fast feedback and continuous delivery practices as the mechanism. The failure measure behaved differently in the early data: change fail rate did not correlate in 2014 and was excluded from the 2014-2017 construct. That history helps explain today's framework: five metrics in two groups, **Throughput** (Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time) and **Instability** (Change Fail Rate, Deployment Rework Rate). MTTR (historical) became Failed Deployment Recovery Time in 2023. Deployment Rework Rate was added in 2024. DORA's 2024 report describes the throughput factor, which includes Failed Deployment Recovery Time, as measuring "the speed of making updates of any kind, normal changes and changes in response to a failure" (p. 12). In 2025 the performance tiers gave way to seven team profiles (2025 report, pp. 15-18).

DORA's own pitfall list covers targets, a single metric, industry as a shield, disparate comparisons, siloed ownership, competing, and measurement over improvement. Independent support for it comes from the Thoughtworks Radar, a practitioner's measurement experience report (Huber, via InfoQ), Goodhart's-law literature and two vendors. Bryan Finster's guidance paper (2022) is published by IT Revolution, a programme domain. It is quoted here only as short fragments from its product page or as summarised by DX, a vendor. It agrees with DORA that the metrics should not be treated as standalone targets or used to compare teams (Findings 5.1, 5.3). SPACE and DevEx are co-authored by Forsgren, so they are not independent.

## Research Methodology
**Search strategy**: The book was read from the new extract at the coordinator-supplied scratch path (`.../54744eb4-.../scratchpad/accelerate-epub/OEBPS/`), treated as untrusted text. Every book quote in this revision was re-checked there (Preface, Foreword 1, Ch 1, 2, 4, 12, 13, 14, 15, Quick Reference, App A, App B). DORA definitions were taken from the raw Markdown source of dora.dev on GitHub (`dora-team/dora.dev`, `hugo/content/guides/dora-metrics/_index.md`). Other sources: dora.dev pages, Google Cloud report posts, and targeted searches limited to domains in `.nwave/trusted-source-domains.yaml`.
**Independence**: See the source-bias metric above. The word "independent" is used only for A5, A6, A7, I2, F1, T1, V1 and V2.
**Quality**: Average reputation 0.92 (27 scored sources; A6 excluded as unverified, A2 excluded as secondary-only). Web content was sanitised and no injected instructions were found.
**Removed in revision 1**: RedMonk (X1). The 2024 Medium-vs-High inversion and the "correlation persists" statement were dropped at that point. Revision 3 restores both, citing the 2024 report PDF directly.
**Revision 2**: The user added the 2024 and 2025 report PDFs to `harness/`, but they could not be rendered then.
**Revision 3**: The coordinator extracted both PDFs to text with macOS PDFKit (`scratchpad/pdftext/dora-2024.txt`, 120 pages; `dora-2025.txt`, 142 pages). The text was read as untrusted data. Citations take the form "(DORA 2024 report, p. N)", where N is the PDF page index; on every page checked it matches the printed page number. Chart text that was scrambled in extraction is not used. Table figures are used only where each row reads cleanly. The 2025 checks used programme web pages instead (G2; dora.dev "DORA 2025: Year in review" [D9]). G1 was re-fetched for the 2022 figures. The Finster product page was re-fetched for verbatim fragments. The definitions were re-fetched at a pinned commit.

## 1. Why measuring software delivery is hard; what makes a good measure

### Finding 1.1: The inventory is invisible and design and delivery overlap
**Evidence**: "Measuring performance in the domain of software is hard—in part because, unlike manufacturing, the inventory is invisible. Furthermore, the way we break down work is relatively arbitrary, and the design and delivery activities—particularly in the Agile software development paradigm—happen simultaneously." (*Accelerate*, Ch 2, chapter opening) [B1]. Independent: Fowler argues there is no meaningful measure of software output and that "false measures only make things worse" (martinfowler.com, 2003) [F1]. DORA-authored (not independent): SPACE, productivity "cannot be reduced to a single dimension or metric" (Forsgren, via InfoQ 2021) [I1].
**Confidence**: Medium (the programme plus one independent author).
**Analysis**: Lean lead time has a design part, the "fuzzy front end" where "it's often unclear when to start the clock", and a delivery part that "is easier to measure and has a lower variability" (*Accelerate*, Ch 2, "Measuring Software Delivery Performance", Table 2.1) [B1]. This is why Change Lead Time starts at commit.

### Finding 1.2: A good measure is a global outcome, not a local output
**Evidence**: Earlier attempts "focus on *outputs* rather than *outcomes*" and "on individual or local measures rather than team or global ones" (*Accelerate*, Ch 2, "The Flaws in Previous Attempts to Measure Performance") [B1]. A successful measure "should focus on a global outcome to ensure teams aren't pitted against each other". The book's example is rewarding developers for throughput and operations for stability, which feeds the "wall of confusion". A measure should also "focus on outcomes not output: it shouldn't reward people for putting in large amounts of busywork" (Ch 2, "Measuring Software Delivery Performance") [B1]. Ch 4, "What Is Continuous Delivery?": "development focuses on throughput, testing on quality, and operations on stability. However, in reality these are all system-level outcomes" [B1]. DORA's pitfall "siloed ownership" asks for all five metrics to be shared across development, operations and release teams [D1]. Independent: Fowler rejects output measures [F1].
**Confidence**: Medium.

### Finding 1.3: Why lines of code, velocity and utilization fail
**Evidence** (*Accelerate*, Ch 2, "The Flaws in Previous Attempts to Measure Performance") [B1]:
- *Lines of code*: "we would prefer a 10-line solution to a 1,000-line solution to a problem"; rewarding it "leads to bloated software".
- *Velocity* (historical term, used here only as the book's example; GLOSSARY says avoid): "designed to be used as a *capacity planning tool*"; "a relative and team-dependent measure, not an absolute one"; contexts "render their velocities incommensurable"; "teams inevitably work to game their velocity".
- *Utilization*: "high utilization is only good up to a point"; "as utilization approaches 100%, lead times approach infinity".
Independent: Fowler on lines of code and output measures [F1]. DORA-authored: activity metrics "should never be used in isolation either to reward or to penalize developers" (Forsgren, via InfoQ 2021) [I1].
**Confidence**: Medium for lines of code and velocity (book plus F1). Medium-Low for utilization (book only, citing queueing theory and Reinertsen).

## 2. The Accelerate research: origins, method, claims, limitations

### Finding 2.1: Origins in the Puppet State of DevOps reports, 2014-2017
**Evidence**: "In late 2013, Nicole, Jez, and Gene started working together with the team at Puppet in preparation for the *2014 State of DevOps Report*"; the book "covers four years of research findings ... (2014 through 2017)". In 2012 Puppet, Kim and Humble had "collected and analyzed 4,000 survey responses" (*Accelerate*, Preface, "The Journey and the Data" and footnote 1) [B1]. "Our research collected over 23,000 survey responses from around the world. We heard from over 2,000 unique organizations" (Preface, "The Research") [B1]. Yearly themes: 2014 foundation; 2015 technical and Lean management practices; 2016 trunk-based development, security and Lean product management; 2017 architecture, transformational leadership and noncommercial outcomes (Preface) [B1]. Corporate history: DORA and Google Cloud announced joint research for the 2018 report in April 2018 (InfoQ, search extract only) [I4]; DORA joined Google Cloud on 2018-12-20 (dora.dev news) [D8]; today DORA is "a program run by Google Cloud" (dora.dev FAQ footer) [D6].
**Confidence**: High (authoritative for its own history).
**Bias note**: Puppet (a DevOps tooling vendor) ran the work in 2014-2017 and its marketing databases were a sampling channel (*Accelerate*, Ch 15). Google Cloud runs it today [D8].

### Finding 2.2: Survey method, psychometrics and latent constructs
**Evidence**: The team moved "from simple yes/no questions to Likert-type questions" (*Accelerate*, Preface, "2014: Laying the Foundation") [B1]. Capabilities are "measured in the form of constructs, using Likert-type questions" (Ch 4, "The Impact of Continuous Delivery") [B1]. "A latent construct is a way of measuring something that can't be measured directly", measured through manifest variables (Ch 13, "Trusting Data with Latent Constructs"). The constructs are checked for discriminant validity, convergent validity and reliability, and "all measures are proxies ... This is just as true of system data as it is of survey data" (Ch 13) [B1]. "It would take several hundred people 'lying' in a coordinated, organized way to make a noticeable difference"; "all responses are anonymous" (Ch 14, "You Can Trust Survey Data") [B1]. Surveys give all respondents "the same items, the same words, and the same definitions" (Ch 14, "Surveys Allow You to Collect and Analyze Data Quickly") [B1]. Independent framing: Sánchez Ruiz et al. note that DORA data is "collected through manual surveys" [A5]. (A6, a single unverified search extract, makes a similar point. It is not counted as support.)
**Confidence**: High as a description of the method. The claim that the data is trustworthy is the programme's own argument.

### Finding 2.3: Cluster analysis found high, medium and low performers every year
**Evidence**: Cluster analysis "categorizes the data without any bias toward 'good' or 'bad'"; "every year, there were significantly different categories of software delivery performance"; the groups "were all significantly different across all four measures" (*Accelerate*, Ch 2, "Measuring Software Delivery Performance") [B1]. "Classification variables are entered into the clustering algorithm and significant groups are identified" (Ch 12, "Classification Analysis") [B1]. "The software delivery performance construct is a combination of three metrics: lead time, release frequency, and MTTR. Change fail rate is not included in the construct, though it is highly correlated with the construct" (App B, "Software Delivery Performance"; MTTR is historical) [B1]. In 2014 "change fail rate did not significantly correlate with the other variables" (dora.dev history, 2026) [D2].
**Confidence**: High as a description of the method (primary source). The clusters are recomputed every year (Finding 3.3).

### Finding 2.4: Claims about organizational performance: prediction, not proven causation
**Evidence**: Respondents rated their organization's relative "profitability, market share, and productivity" on a scale "validated multiple times in prior research (Widener 2007)". High performers were "consistently *twice as likely* to exceed these goals as low performers" (*Accelerate*, Ch 2, "The Impact of Delivery Performance on Organizational Performance"; data 2014-2017) [B1]. For noncommercial goals in 2017 they were "twice as likely to exceed objectives" (same section) [B1]. A follow-up to the 2014 survey found "50% higher market capitalization growth over three years", but "this analysis was not replicated in later years because our dataset was not large enough" (App B, "Organizational Performance") [B1]. Arrows in the figures signify "a predictive relationship ... beyond correlation into prediction" (Ch 2, box "Reading the Figures in This Book") [B1]. The method is inferential prediction with "multiple linear regression or partial least squares regression", used "when purely experimental design is not possible". Predictive, causal and mechanistic analysis "were not included in our research, because we did not have the data necessary"; causal analysis "generally requires randomized studies" (Ch 12, "Inferential Predictive Analysis" and "Predictive, Causal, and Mechanistic Analysis") [B1]. DORA today calls the metrics "leading indicators" for organizational performance and well-being [D1].
**Confidence**: High that this is what the book claims and how it reached the claim. A *causal* reading is not supported by the authors' own design.
**Interpretation (labelled)**: Good Software Delivery Performance goes with better organizational outcomes in cross-sectional survey data. The research does not show that improving the metrics will by itself raise profit.

### Finding 2.5: The capabilities model
**Evidence**: "Our research has identified 24 key capabilities that drive improvement in software delivery performance" (*Accelerate*, Ch 1, "Evidence-Based Transformations Focus on Key Capabilities"). They are "classified into five categories" (Quick Reference; App A) [B1]. Maturity models "are not the appropriate tool to use or mindset to have"; capability models are "multidimensional and dynamic" and "outcome based"; maturity models "end up being vanity metrics" (Ch 1, "Focus on Capabilities, Not Maturity") [B1]. CD capabilities, "when taken together", have "a strong positive impact on software delivery performance" and decrease deployment pain and burnout (Ch 4, "The Impact of Continuous Delivery") [B1]. DORA today calls the metrics "lagging indicators" for development and delivery practices [D1].
**Confidence**: High as a description of the model. The "drive" relationships are inferential (Finding 2.4).

### Finding 2.6: Limitations and critiques
**Evidence (the authors')**: "A cross-sectional design means the data was collected at a single point in time. However, it precluded us from longitudinal analysis" (*Accelerate*, Ch 15, footnote 1). Recruitment used nonprobability snowball sampling via the authors', Puppet's, Kim's and Humble's mailing lists and social media. "We miss a cohort that are likely performing even worse than our low performers". Respondents "might want to paint their team or organization in a favorable light", which the authors mitigated by asking about practices, never "if they practiced continuous integration" (all Ch 15, "The Data for the Project") [B1]. DORA FAQ: some year-to-year differences "may be artifacts of sampling and analysis methods"; DORA does "not share the raw data" (2025) [D6].
**Evidence (programme-published caveat)**: Fowler's foreword: "they are still surveys that capture subjective perceptions, and I wonder how their population sample reflects the general IT world. I'll have more confidence in their results when other teams, using different approaches, are able to confirm their reasoning"; "confirmation bias is a strong force"; the book "focuses on IT delivery, that is, the journey from commit to production, not the entire software development process"; the earlier reports' missing method "greatly undermined their credibility" (Foreword by Martin Fowler) [B1-F]. Fowler is a different author, but the foreword is published in the programme's book.
**Evidence (independent)**: Sánchez Ruiz et al. (arXiv preprint, 2023): "the DORA benchmark cannot be applied to OSS projects" because open source focuses on "continuous release of code" rather than deployment to production [A5]. (A6, a single unverified search extract, says aggregate metrics can mask differences between systems. It is not counted as support.)
**Confidence**: High that self-report, nonprobability sampling, cross-sectional design and sponsorship are the main limitations. The authors state them, and one independent preprint [A5] echoes the survey point. **No independent replication** of the findings was found.

## 3. Why Throughput and Instability move together

### Finding 3.1: The core finding (Accelerate data, 2014-2017)
**Evidence**: "there is no tradeoff between improving performance and achieving higher levels of stability and quality. Rather, high performers do better at *all* of these measures" (*Accelerate*, Ch 2, "Measuring Software Delivery Performance") [B1]. "There are no trade-offs between improving performance and achieving higher levels of tempo and stability: they move in tandem" (App B, "Software Delivery Performance") [B1]. "We also found that throughput and stability move together" (Preface, "2014: Laying the Foundation") [B1]. Ratios for 2017, high vs low performers (historical metric names): "46 times more frequent code deployments", "440 times faster lead time from commit to deploy", "170 times faster mean time to recover from downtime", "5 times lower change failure rate" (Ch 1, "The Value of Adopting DevOps") [B1]. DORA today: "DORA's research has repeatedly demonstrated that speed and stability are not tradeoffs" [D1]. Endorsement: Fowler, "speed depends on stability, so good IT practices give you both" (Foreword, printed in the programme's book) [B1-F]. This endorses the claim but does not test it. Thoughtworks lists the metrics as a technique on its Radar, but does not address the trade-off claim, so it is not cited as evidence here.
**Confidence**: **Medium. This is a programme finding, not independently replicated.** It is endorsed in Fowler's foreword (printed in the programme book), and Thoughtworks lists the metrics as a technique; neither tests the trade-off claim.
**Correlation vs causation**: The finding is cluster-level co-occurrence in cross-sectional survey data. It shows that Throughput and Instability are not opposed across the population. It does not show that higher Throughput *causes* lower Instability.

### Finding 3.2: Mechanisms (proposed by the authors)
**Evidence**:
- The authors propose that **small batches** are central. Deployment frequency is used "as a proxy for batch size", and "deployment frequency is the reciprocal of batch size" (*Accelerate*, Ch 2, "Measuring Software Delivery Performance" and footnote 2) [B1]. Working in small chunks gives "essential feedback on the work we are doing so that we can course correct" (Ch 4, "What Is Continuous Delivery?") [B1]. DORA today recommends reducing batch size as a common way to improve all five metrics (paraphrased) [D1].
- The authors propose that **fast feedback and continuous delivery** link the two groups. CD means "creating multiple feedback loops" (Ch 4, "What Is Continuous Delivery?"); "continuous delivery predicts lower change fail rates" and "lower levels of unplanned work and rework" (Ch 4, "The Impact of Continuous Delivery on Quality") [B1]. The book's percentages for unplanned work have been dropped: neither Ch 4 nor App B gives the survey year.
- The authors propose that **fixes ship fast** when lead times are short, "when there is a defect or outage and we need to deliver a fix rapidly and with high confidence" (Ch 2) [B1].
- 2024 (programme): AI adoption came with "an estimated decrease in delivery throughput by 1.5%, and an estimated reduction in delivery stability by 7.2%". DORA's reading is that improvement needs "the basics of successful software delivery, like small batch sizes and robust testing mechanisms" (Google Cloud blog, 2024-10-23) [G4]. The report text gives the hypothesis directly: AI may have made "the field to forget one of DORA's most basic principles—the importance of small batch sizes", because "changelists are growing in size"; "DORA has consistently shown that larger changes are slower and more prone to creating instability" (DORA 2024 report, p. 40) [R24]. 2025: "Without robust control systems, like strong automated testing, mature version control practices, and fast feedback loops, an increase in change volume leads to instability" [G2].
- Independent, anecdotal: Huber's experience report (as reported by Linders, InfoQ 2021) [I2].
**Confidence**: Medium-Low. The mechanisms are the authors' proposal, tested only inferentially inside the programme.

### Finding 3.3: Exceptions and year-to-year nuance
**Evidence** (each with report year):
- **2014**: change fail rate "did not significantly correlate with the other variables" [D2]. In the 2014-2017 analysis it stayed outside the delivery construct, though "highly correlated with" it (*Accelerate*, App B) [B1].
- **2016**: "medium performers do worse than low performers on change fail rate"; "Our research doesn't conclusively explain this"; hypothesis: medium performers are "racking up technical debt" (Ch 2, box "Surprise!") [B1]. The box ties this to "the 2016 study, where we found that medium performers spend more time on unplanned rework than low performers". App B, "Quality", calls it "evidence of the J-curve". App B's percentage is dropped here because it gives no year [B1].
- **2017**: "we saw low performers lose some ground in stability", suspected to come from "attempts to increase tempo ('work harder!')" (Ch 2) [B1].
- **2022**: "there was no evidence of an 'Elite' cluster"; "High performers are at a four-year low and Low performers rose dramatically from 7% in 2021 to 19% in 2022!"; "The Medium cluster, however, swelled to 69% of respondents" (2022 report data, confirmed by re-fetching G1 on 2026-10-17; the High share appears only in the post's table image and was not captured). The hypothesis offered is the pandemic. The "Slowing" operational cluster "do not deploy too often, but when they do, they are likely to succeed" (Google Cloud blog, 2022-09-29) [G1]. The DORA FAQ allows for "artifacts of sampling and analysis methods" [D6].
- **2023**: Elite returned; "Elite performers around the world are able to achieve both throughput and stability" (Google Cloud blog, 2023-10-05) [G3, prior run].
- **2024 (verified in the PDF)** [R24]:
  - **Clusters.** The clustering used "the original four software delivery metrics to remain consistent with previous years' cluster analyses". "Four distinct clusters emerged" (DORA 2024 report, p. 13). Shares, with 89% uncertainty intervals (p. 13):

    | Cluster | Share | Change lead time | Deployment frequency | Change fail rate | Failed deployment recovery time |
    |---|---|---|---|---|---|
    | Elite | 19% (18-20%) | less than one day | on demand (multiple deploys per day) | 5% | less than one hour |
    | High | 22% (21-23%) | between one day and one week | between once per day and once per week | 20% | less than one day |
    | Medium | 35% (33-36%) | between one week and one month | between once per week and once per month | 10% | less than one day |
    | Low | 25% (23-26%) | between one month and six months | between once per month and once every six months | 40% | between one week and one month |

    The table text extracted cleanly. The companion chart, Figure 1 on p. 14, is extraction unclear and is not used.
  - **Inversion verified.** The Medium change fail rate (10%) is lower than the High one (20%) (p. 13). The text explains: "This correlation persists even in the medium performance cluster (orange), where throughput is lower and stability is higher than in the high performance cluster (yellow)"; "We made a decision to call the faster teams 'high performers,' and the slower but more stable teams 'medium performers'" (p. 14).
  - **Correlation verified.** "Within all four clusters, throughput and stability are correlated" (p. 14). Also: "More than half of the teams in our study this year show differences in software throughput and software stability" (p. 11). And: "While the traditional association between throughput and stability has persisted, emerging evidence suggests these factors operate with sufficient independence to warrant separate consideration" (p. 39).
  - **Elite vs Low ratios**: "127x faster lead time", "182x more deployments per year", "8x lower change failure rate", "2293x faster failed deployment recovery times" (p. 15).
  - **AI**: "an estimated 1.5% reduction" in throughput and "an estimated 7.2% reduction" in stability "for every 25% increase in AI adoption" (p. 40).
  - **Platform engineering**: "approximately an 8% decrease" in throughput (p. 53) and "a surprising 14% decrease in change stability" (p. 54) for platform users compared with non-users.
- **2025 (verified in the PDF)** [R25]:
  - **AI.** "AI adoption now improves software delivery throughput, a key shift from last year. However, it still increases delivery instability" (DORA 2025 report, p. 4, Key findings). "AI's relationship with software delivery throughput has turned from negative to positive" (p. 42). "AI is associated with an increase in software delivery instability" (p. 39). Consistent with the Google Cloud post [G2] and the year-in-review [D9]. Note that p. 35 restates the 2024 result as "an estimated 7.2% increase in software delivery instability", whereas the 2024 report itself says "reduction in delivery stability" (2024 report, p. 40).
  - **Why profiles.** Delivery metrics "tell you what is happening, but they don't explain why" (p. 14). The clustering used team performance, individual effectiveness, product performance, valuable work, friction, burnout, software delivery throughput and software delivery instability (p. 15). "The names and descriptions for each of these clusters are an interpretation of the data" (p. 16).
  - **All seven profiles**, with share of respondents (2025 report, pp. 16-18; descriptions quoted from the report's own one-line summaries):
    1. **Foundational challenges** (10%, p. 16): "stuck in survival mode"; "notable challenges with the stability of the software and operational environment".
    2. **The legacy bottleneck** (11%, p. 17): "in a constant state of reaction, where unstable systems dictate their work and undermine their morale".
    3. **Constrained by process** (17%, p. 17): "running on a treadmill. Despite working on stable systems, their effort is consumed by inefficient processes".
    4. **High impact, low cadence** (7%, p. 17). The description is extraction unclear. Its fragments ("high-impact work, reflected in strong product performance and high individual effectiveness"; "low software delivery throughput and high instability") sit on non-adjacent lines among chart labels. Quote only the name and share.
    5. **Stable and methodical** (15%, p. 18): "the steady artisans of the software world, delivering high-quality, valuable work at a deliberate and sustainable pace".
    6. **Pragmatic performers** (20%, p. 18). The description is extraction unclear: the sentence beginning "These teams consistently deliver work with impressive speed and stability" is split by the chart label "Stable and methodical". Quote only the name and share.
    7. **Harmonious high-achiever** (20%, p. 18): "a virtuous cycle where a stable, low-friction environment empowers teams to deliver high-quality work sustainably and without burnout".
  - The shares sum to 100%. Text order in the extraction is partly scrambled by the page layout. Shares were re-checked in revision 4:
- The legacy bottleneck: "11% of survey respondents are in cluster 2" on adjacent lines (p. 17).
- Stable and methodical: "15% of survey respondents are in cluster 5" on adjacent lines (p. 18).
- High impact, low cadence: "Percentage of respondents: 7% of" and "survey respondents are in cluster 4." are separated by one interleaved line (p. 17). It is readable and consistent with the 100% total, but slightly less clean.
Doc writer: for profiles 4 and 6, quote only names and shares.
**Confidence**: High that DORA reported these (primary statements). The explanations DORA offers are hypotheses.
**Interpretation (labelled)**: "No trade-off" holds at the population level and for top performers. Middle clusters, specific teams and specific interventions (AI, platform adoption) can show Throughput and Instability moving apart. This is consistent with DORA reporting them as separate factors since 2024.

## 4. The DORA framework today

### Finding 4.1: The five metrics and two groups, verbatim (credit: DORA)
**Source**: DORA, "DORA's software delivery performance metrics", Nathen Harvey. Front matter: `date: 2024-03-29`, `updated: 2026-01-05` [D1]. Verified 2026-10-17 against the raw Markdown source at `https://raw.githubusercontent.com/dora-team/dora.dev/main/hugo/content/guides/dora-metrics/_index.md`. Re-checked the same day at a pinned commit: `https://raw.githubusercontent.com/dora-team/dora.dev/7a6be9730c592a386a83d3b417b1d4859d736853/hugo/content/guides/dora-metrics/_index.md`. Commit `7a6be97` (2026-03-12) is the latest commit touching the file, per GitHub's commit history. Its message is "Migrate history of software delivery metrics to an Insight", a structural change that moved the history content to `/insights/`. The page's front-matter `updated: 2026-01-05` was not bumped: the `main` fetch, which is that commit's content, still shows it. That is why the commit date and D1's "updated" date differ. I did not trace whether the definition lines changed in any of the recent commits (`67a7603` 2026-01-02, `6b46d7a` 2026-02-23, `7a6be97` 2026-03-12). The fetch tool caps quotes at 125 characters, so long lines were retrieved in two consecutive parts and joined. The pinned-commit fetch and the `main` fetch gave identical text. Re-check against the live page before publishing.
- `### Throughput`: "Throughput is a measure of how many changes can move through the system over a period of time." DORA uses three factors:
  - **Change lead time**: "The amount of time it takes for a change to go from committed to version control to deployed in production."
  - **Deployment frequency**: "The number of deployments over a given period or the time between deployments."
  - **Failed deployment recovery time**: "The time it takes to recover from a deployment that fails and requires immediate intervention."
- `### Instability`: "Instability is a measure of how well the software deployments go." DORA uses two factors:
  - **Change fail rate**: "The ratio of deployments that require immediate intervention following a deployment. Likely resulting in a rollback of the changes or a “hotfix” to quickly remediate any issues."
  - **Deployment rework rate**: "The ratio of deployments that are unplanned but happen as a result of an incident in production."
- "DORA’s research has repeatedly demonstrated that speed and stability are not tradeoffs."

**Wording differences from GLOSSARY.md** (for the doc writer and glossary owner):
| Term | GLOSSARY.md | dora.dev (2026-01-05) |
|---|---|---|
| Change Lead Time | "The time a change takes to go from committed..." | "The amount of time it takes for a change to go from committed..." |
| Deployment Frequency | "...over a given period, or the time..." (comma) | "...over a given period or the time..." (no comma) |
| Failed Deployment Recovery Time | identical | identical |
| Change Fail Rate | "...immediate intervention following deployment." | "...immediate intervention following a deployment. Likely resulting in a rollback of the changes or a “hotfix”..." |
| Deployment Rework Rate | "...that are unplanned and happen as a result..." | "...that are unplanned but happen as a result..." |
| Throughput (group) | "how fast changes move through the delivery process" | "how many changes can move through the system over a period of time" |
| Instability (group) | "how often deployments go wrong" | "how well the software deployments go" |
| Term casing | Title Case (Change Lead Time) | sentence case (Change lead time) |
**Confidence**: High (authoritative for its own definitions; raw source checked).

### Finding 4.2: From four keys to five metrics
**Evidence** (Harvey, "A history of DORA's software delivery metrics", dora.dev, 2026-01-02) [D2]:
- 2014: four variables; change fail rate "did not significantly correlate with the other variables", so IT performance used three metrics.
- 2015: two groups, throughput (deployment frequency, lead time) and stability (MTTR, change fail rate). These are the historical group and metric names.
- 2018: availability added; the umbrella became "Software Delivery and Operational (SDO) performance". 2021: reliability was wrongly called a "fifth metric"; it measures operational performance, not delivery.
- 2023: MTTR renamed **Failed Deployment Recovery Time**, because earlier definitions did not "distinguish between a failure initiated by a software change" and external failures.
- 2024: **Deployment Rework Rate** added to test whether change fail rate was a proxy for rework. The two factors became "Software Delivery Throughput" and "Software Delivery Instability".
- 2025: no metric change recorded on the history page.
**From the 2024 report itself** [R24]:
- Change failure rate "has long had an outlier" status; it is "strongly correlated with the other three metrics but statistical tests and methods prevent us from combining all four into one factor" (DORA 2024 report, p. 11).
- The rework question: "For the primary application or service you work on, approximately how many deployments in the last six months were not planned but were performed to address a user-facing bug in the application?"; "rework rate and change failure rate are related. Together, these two metrics create a reliable factor of software delivery stability" (p. 11).
- **How DORA describes the factors (Gap 3: description found)**: DORA's 2024 report describes the throughput factor as measuring "the speed of making updates of any kind, normal changes and changes in response to a failure", and the stability factor as measuring "the likelihood deployments unintentionally lead to immediate, additional work" (p. 12). The pages read contain no statistical test of where recovery time belongs.
- **Naming**: the 2024 report calls the second factor "software delivery stability" (pp. 11-12). The dora.dev history [D2], the metrics guide [D1] and the 2025 report (p. 15, "Software delivery instability") use "instability". See Conflict 8.
- The cluster analysis still used the original four metrics, not five (p. 13).
2024 survey (dora.dev, re-fetched 2026-10-17) [D4]: the preamble reads "For the primary application or service you work on..."; the recovery question asks "How long does it generally take to restore service after a change to production"; the rework question asks "Approximately what percentage of deployments in the last 6 months were not planned". The lead-time answer bands are the same six as *Accelerate* Ch 2, plus "I don't know or NA".
**Confidence**: High.

### Finding 4.3: Capabilities -> Software Delivery Performance -> outcomes
**Evidence**: The metrics are leading indicators for organizational performance and well-being and lagging indicators for practices [D1]. In the book, capabilities predict Software Delivery Performance, which predicts organizational and noncommercial performance (*Accelerate*, Ch 1; Ch 2, Figure 2.4; App A) [B1]. 2024: teams should "replicate our findings within your specific context" and use them "as a hypothesis for your experiments and continuous improvement initiatives" [G4].
**Confidence**: High as a description of DORA's model. The links are inferential (Finding 2.4).

### Finding 4.4: DORA's current guidance on use
**Evidence** (dora.dev 2026, paraphrased) [D1]: measure one application or service at a time; gather the cross-functional team; set a baseline with the Quick Check; discuss friction and map the value stream; commit to the biggest constraint; plan with leading indicators; do the work; re-check; repeat. Independent: the Thoughtworks Radar says to use the metrics "for team reflection and learning rather than just building complex dashboards" (Apr 2026) and to "consider just regularly taking the DORA quick check in team retrospectives" (Oct 2021, Mar 2022) [T1]. Huber's experience report (as reported by Linders, InfoQ 2021): measuring was "more time-consuming than I thought" [I2].
**Confidence**: High.

## 5. Common pitfalls

DORA's own list (dora.dev, 2026) [D1], paraphrased: (1) setting metrics as a goal (Goodhart's law); (2) one metric to rule them all; (3) using industry as a shield; (4) making disparate comparisons; (5) siloed ownership; (6) competing; (7) focusing on measurement at the expense of improvement.

**Note on Finster [P1]**: The full PDF was not obtained (it is a product download). Quotes marked "as summarised by DX (V1), 2022" come from Abi Noda's newsletter summary, and DX is a vendor. Quotes marked "P1 product page" are short fragments from IT Revolution's product page. They were re-fetched on 2026-10-17 with a request for character-for-character copies, but the fetch tool summarises pages and caps quotes at 125 characters, so treat them as near-verbatim and re-check on the live page before quoting. P1 is published on a programme domain (itrevolution.com) and is not counted as independent.

### Finding 5.1: Metrics as targets get gamed (Goodhart)
**Evidence**: DORA pitfall 1 [D1]. Independent academic: overoptimization of a proxy is "sometimes termed Goodhart's Law", with "(at least) four different mechanisms" (Manheim and Garrabrant, arXiv 2018) [A7]. Finster: the metrics "are often misapplied as standalone improvement targets", leading to "deploying code hastily at the expense of quality" (P1 product page fragments) [P1]; "The goal isn't better DORA metrics" (as summarised by DX (V1), 2022) [V1]. Vendor corroboration: "teams might deploy trivial changes to boost frequency" and "declare incidents resolved prematurely to improve recovery time" (LinearB) [V2]. Book: velocity gets gamed when used as productivity (*Accelerate*, Ch 2) [B1].
**Confidence**: Medium. The only independent non-vendor source (A7) is about Goodhart's law in general, not about DORA metrics.

### Finding 5.2: Reading one metric, or one group, alone
**Evidence**: DORA pitfall 2 [D1]. "Measuring deployment frequency without using quality metrics as guardrails will result in poor outcomes" (Finster, as summarised by DX (V1), 2022) [V1]. DORA-authored: productivity "cannot be reduced to a single dimension or metric" [I1]. 2025: Throughput up and stability down with AI adoption [G2].
**Confidence**: Medium (no independent non-vendor source).

### Finding 5.3: Comparing teams, league tables, competing
**Evidence**: DORA pitfalls 4 and 6; metrics are best for "one application or service at a time" [D1]. "Comparing your metrics year-over-year is more meaningful than comparing yourself to other companies" (2023) [G3]. Finster: the metrics are for a team's own improvement "rather than for comparing teams to each other" (P1 product page fragment) [P1]; "We heard about directors and VPs comparing teams based on the metrics" (as summarised by DX (V1), 2022) [V1]. A6 is not used. Book: a good measure must not pit teams against each other, and some managers have used velocity "to compare teams" (*Accelerate*, Ch 2) [B1]. The 2025 report: "the best, most insightful comparisons of software delivery performance are for the same application or service over time. The goal is continuous learning and improvement, not necessarily achieving top software delivery performance" (DORA 2025 report, p. 20) [R25]. The 2024 report: "Improving should be more important to a team than reaching a particular performance level. The best teams are those that achieve elite improvement, not necessarily elite performance" (DORA 2024 report, p. 14) [R24].
**Confidence**: Medium (the programme is consistent across years; no independent non-vendor source).

### Finding 5.4: Measuring individuals
**Evidence**: The survey and definitions work at team and service level: "For the primary application or service you work on" [D4]; the same scope appears in *Accelerate* Ch 2 [B1]. DORA-authored: activity metrics "should never be used in isolation either to reward or to penalize developers" [I1]. Vendor: the metrics are "indicators of team productivity, not individual developer performance" (LinearB) [V2]. Finster's product page says the paper "Guides readers on nurturing a learning culture and avoiding the pitfalls of measuring individuals" (P1 product page, Features section, re-fetched 2026-10-17; see the caveat above) [P1]. The PDF itself was not read. DORA's metrics page has no explicit statement on individuals.
**Confidence**: Medium-Low.

### Finding 5.5: Ignoring context and application type; chasing benchmarks
**Evidence**: DORA pitfall 4: comparing, for example, a mobile app with a mainframe system misleads [D1]. Independent: "the DORA benchmark cannot be applied to OSS projects" without adaptation (arXiv preprint, 2023) [A5]. Benchmarks are yearly snapshots: the respondents differ each year [D6]; Elite was absent in 2022 and back in 2023 [G1], [G3]; the tiers became profiles in 2025 [G2]. Counterweight, DORA pitfall 3: regulated and large organisations appear in every cluster (*Accelerate*, App B, "Other", 2017 data) [B1], [D1]. The 2024 report agrees: "Our research rarely finds that industry is a predictor of software delivery performance; we see high-performing teams in every industry vertical" (DORA 2024 report, p. 15) [R24]. On which group matters more: "There may not be a universal answer to this question. It depends on the application or service being considered, the goals of the team working on that application, and most importantly the expectations of the application's users" (p. 14).
**Confidence**: Medium.

### Finding 5.6: Measuring without acting; tooling-first
**Evidence**: DORA pitfall 7 [D1]. Independent: the Thoughtworks Radar warns against spending "weeks to build up sophisticated dashboard tooling" (2021) and calls pipeline-only approaches "misguided" because "Stability metrics only make sense if they include data about real incidents that degrade service for the users" (2021, 2022) [T1]. Huber's experience report (as reported by Linders, InfoQ 2021): change fail rate was hardest because of "no link between a deployment and a system impairment" [I2]. Finster, as summarised by DX (V1), 2022: the metrics "don't fix things"; "vanity radiators"; "two days every month gathering delivery metrics"; "More commercial tools are including DORA metrics, but the context is being lost" [V1].
**Confidence**: High (DORA plus two independent non-vendor sources).

### Finding 5.7: Treating the five metrics as the whole of productivity
**Evidence**: DORA 2025: "Simple software delivery metrics alone aren't sufficient. They tell you what is happening but not why it's happening" [G2]. Fowler's foreword: commit-to-production only, "not the entire software development process" [B1-F]. Finster, as summarised by DX (V1), 2022: "only one aspect of the health of a system" [V1]. DORA-authored: SPACE's five dimensions and "a reduced set of metrics that span across all three levels" [I1]; DevEx, "neither perceptual nor workflow measures alone can tell the full story" (Noda, InfoQ 2023; Noda founded DX, a vendor) [I3]. Independent, by implication: Fowler [F1].
**Confidence**: Medium.

### Finding 5.8: Culture: fear produces wrong numbers
**Evidence**: "in pathological and bureaucratic organizational cultures, measurement is used as a form of control ... As Deming said, 'whenever there is fear, you get the wrong numbers'" (*Accelerate*, Ch 2, "Driving Change", quoting Humble et al. 2014) [B1]. Data should be collected "without telling everyone they must answer positively *or else*" (Ch 14, footnote 1) [B1]. DORA-authored: "Metrics influence decisions and behavior" [I1]. Related (not direct support): Goodhart's-law mechanisms [A7].
**Confidence**: Medium.

## Source Analysis

All accessed 2026-10-17. Scores per `.nwave/trusted-source-domains.yaml`. Independence class: **Prog** = DORA programme; **DA** = DORA-authored (Forsgren); **Ind** = independent.

| ID | Source | URL | Domain | Class | Reputation | Verification status |
|----|--------|-----|--------|-------|-----------|---------------------|
| B1 | Forsgren, Humble, Kim, *Accelerate* (2018) | local EPUB | book | Prog | 1.0 | All quotes re-checked against the new extract this run |
| B1-F | Fowler, Foreword 1 to *Accelerate* | (in B1) | book | Prog | 1.0 | Re-checked this run |
| D1 | DORA, "DORA's software delivery performance metrics" (upd. 2026-01-05) | https://dora.dev/guides/dora-metrics/ | dora.dev | Prog | 1.0 | Raw GitHub source checked this run |
| D2 | Harvey, "A history of DORA's software delivery metrics" (2026-01-02) | https://dora.dev/guides/dora-metrics/history/ | dora.dev | Prog | 1.0 | Fetched this run |
| D3 | DORA, 2024 report page | https://dora.dev/research/2024/dora-report/ | dora.dev | Prog | 1.0 | Fetched this run |
| D4 | DORA, 2024 survey questions | https://dora.dev/research/2024/questions/ | dora.dev | Prog | 1.0 | Re-fetched this run |
| D6 | DORA, FAQ (upd. 2025-10-06) | https://dora.dev/faq/ | dora.dev | Prog | 1.0 | Fetched this run |
| D8 | DORA Team, "DORA joins Google Cloud" (2018-12-20) | https://dora.dev/news/dora-joins-google-cloud/ | dora.dev | Prog | 1.0 | Fetched this run |
| D9 | DORA, "DORA 2025: Year in review" (date not captured) | https://dora.dev/insights/dora-2025-year-in-review/ | dora.dev | Prog | 1.0 | Fetched revision 2 |
| G1 | DeBellis, Peters, 2022 report post (2022-09-29) | https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/ | cloud.google.com | Prog | 1.0 | Re-fetched revision 2 (2022 percentages confirmed) |
| R24 | DORA, *Accelerate State of DevOps Report 2024* (PDF) | `harness/2024-dora-accelerate-state-of-devops-report.pdf` | local | Prog | 1.0 | Read revision 3 (PDFKit text, `scratchpad/pdftext/dora-2024.txt`); pp. 9-16, 39-40, 53-54. **Provenance**: downloaded from https://dora.dev/research/2024/ (PDF link https://dora.dev/research/2024/dora-report/2024-dora-accelerate-state-of-devops-report.pdf); SHA-1 `ecec8c87dfad90fd9f6c9e93d053b40f4c404a51`, identical to services.google.com/fh/files/misc/2024_final_dora_report.pdf. Listed under `primary_research.local_files` in `.nwave/trusted-source-domains.yaml` |
| R25 | DORA, *State of AI-assisted Software Development 2025* (PDF) | `harness/2025_state_of_ai_assisted_software_development.pdf` | local | Prog | 1.0 | Read revision 3 (PDFKit text, `scratchpad/pdftext/dora-2025.txt`); pp. 4, 14-20, 35, 39, 42. **Provenance**: from https://dora.dev/research/2025/ (download hosted on Google Drive); SHA-1 e32056014be5ef0aa14e0557e9e234b3488fd6a0; publisher DORA/Google Cloud. Listed under `primary_research.local_files` in `.nwave/trusted-source-domains.yaml` |
| G2 | Harvey, DeBellis, 2025 report post (2025-09-23) | https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report | cloud.google.com (now trusted) | Prog | 1.0 | Fetched this run |
| G3 | DeBellis, Harvey, 2023 report post (2023-10-05) | https://cloud.google.com/blog/products/devops-sre/announcing-the-2023-state-of-devops-report | cloud.google.com | Prog | 1.0 | Prior run (same day); not re-fetched |
| G4 | Harvey, DeBellis, "Highlights from the 10th DORA report" (2024-10-23) | https://cloud.google.com/blog/products/devops-sre/announcing-the-2024-dora-report | cloud.google.com | Prog | 1.0 | Fetched this run |
| P1 | Finster, "How to Misuse & Abuse DORA Metrics" (May 2022) | https://itrevolution.com/product/how-to-misuse-abuse-dora-metrics/ | itrevolution.com | Prog (domain) | 0.8 | Product page re-fetched revision 2 (fragments); PDF not obtained |
| A1 | Forsgren, Kersten, "DevOps Metrics", CACM 61(4), 2018 | https://queue.acm.org/detail.cfm?id=3182626 | acm.org | DA | 1.0 | [Restricted Access]; abstract-level, prior run |
| A2 | Forsgren et al., "The SPACE of Developer Productivity", ACM Queue 2021 | https://queue.acm.org/detail.cfm?id=3454124 | acm.org | DA | n/a (excluded from average) | Via I1 (secondary); 403 on full text |
| I1 | De Simone, SPACE article, InfoQ (2021-03-18) | https://www.infoq.com/news/2021/03/space-developer-productivity | infoq.com | DA | 0.8 | Fetched this run |
| I3 | Noda, "DevEx, a New Metrics Framework...", InfoQ (2023-05-16) | https://www.infoq.com/articles/devex-metrics-framework/ | infoq.com | DA (+vendor author) | 0.8 | Fetched this run |
| I4 | InfoQ, Forsgren on DORA and Google collaboration (2018-04) | https://www.infoq.com/news/2018/04/DORA-Google-Cloud-New-Research/ | infoq.com | DA | 0.8 | Search extract only |
| A5 | Sánchez Ruiz et al., arXiv 2304.14790 (2023) | https://arxiv.org/abs/2304.14790 | arxiv.org | Ind | 1.0 | Abstract fetched; preprint |
| A6 | "Fully Automated DORA Metrics Measurement for Continuous Improvement", ICSSP 2024, doi 10.1145/3666015.3666020 | https://dl.acm.org/doi/fullHtml/10.1145/3666015.3666020 | acm.org | Ind | n/a (excluded from average) | **Unverified search extract, authors unknown** (403) |
| A7 | Manheim, Garrabrant, "Categorizing Variants of Goodhart's Law", arXiv 1803.04585 | https://arxiv.org/abs/1803.04585 | arxiv.org | Ind | 1.0 | Abstract fetched |
| I2 | Linders, reporting Nikolaus Huber's experience, InfoQ (2021-08-12) | https://www.infoq.com/news/2021/08/measuring-four-key-metrics/ | infoq.com | Ind | 0.8 | Fetched this run |
| F1 | Fowler, "Cannot Measure Productivity" (2003-08-29) | https://martinfowler.com/bliki/CannotMeasureProductivity.html | martinfowler.com | Ind | 0.8 | Prior run (same day); [Published 2003] |
| T1 | Thoughtworks Technology Radar, "DORA metrics" (2018-2026) | https://www.thoughtworks.com/en-gb/radar/techniques/dora-metrics | thoughtworks.com | Ind | 0.8 | Fetched this run |
| V1 | Noda, summary of P1, DX newsletter (2022-07-22) | https://newsletter.getdx.com/p/misuse-dora | getdx.com | Ind (vendor) | 0.6 | Fetched; commercial interest |
| V2 | Pearson, LinearB (2024-08-22, upd. 2025-04-08) | https://linearb.io/blog/dora-metrics | linearb.io | Ind (vendor) | 0.6 | Fetched; commercial interest |

Reputation (27 scored; A6 and A2 excluded): 1.0: 18 | 0.8: 7 | 0.6: 2 | **Average 0.92**. **Bias**: 21/29 (72%) not independent (16 Prog, 5 DA); 8/29 (28%) independent, of which 2 are vendors and 1 (A6) is unverified and supports nothing. Removed: X1 (RedMonk). Rejected as untrusted: dzone, hackernoon, zbmowrey.com, stride.page, an unattributed dev.to post, Wikipedia.

### Confidence per sub-topic (revision 2)
| Sub-topic | Confidence | Why |
|---|---|---|
| 1. Why hard; good measures | Medium (Medium-Low for utilization) | Programme plus one independent author (Fowler 2003) |
| 2. Accelerate research | High as a description of origins, method, claims and limitations; Low for external validation | No independent replication; the only independent critique used is a preprint (A5) |
| 3. Throughput and Instability together | Medium for the trend (programme finding, not independently replicated; endorsed only in Fowler's foreword); Medium-Low for mechanisms; High that DORA reported the dated exceptions, including 2024 cluster detail and 2025 profiles (now read in the PDFs) | Revision 3: 2024 and 2025 claims verified in the primary reports; the trend's rating is unchanged because the PDFs are programme sources |
| 4. DORA framework today | High | Authoritative for its own definitions (raw source at pinned commit) |
| 5. Pitfalls | 5.6 High; 5.1, 5.2, 5.3, 5.5, 5.7, 5.8 Medium; 5.4 Medium-Low | Independent non-vendor support exists mainly for tooling and dashboards (Thoughtworks, Huber) |

### Revision 3 PDF checks (from the PDFKit text extraction)
| # | Item | Result | Page |
|---|---|---|---|
| 1 | 2024 Medium-vs-High Change Fail Rate inversion | **Verified.** High 20%, Medium 10%; "throughput is lower and stability is higher than in the high performance cluster"; slower but more stable teams were named "medium performers" | DORA 2024 report, pp. 13-14 |
| 2 | 2024 report says Throughput and Instability still correlate | **Verified, with nuance.** "Within all four clusters, throughput and stability are correlated. This correlation persists even in the medium performance cluster". But "More than half of the teams ... show differences in software throughput and software stability" (p. 11), and the factors "operate with sufficient independence to warrant separate consideration" (p. 39) | pp. 11, 14, 39 |
| 3 | 2024 cluster shares | **Verified.** Elite 19% (18-20%), High 22% (21-23%), Medium 35% (33-36%), Low 25% (23-26%); 89% uncertainty intervals. Clustering used the original four metrics | p. 13 |
| 4 | Why Failed Deployment Recovery Time is in Throughput | **Description found; no statistical test of recovery time's placement in the pages read.** DORA describes the throughput factor as measuring "the speed of making updates of any kind, normal changes and changes in response to a failure". (Separately, p. 11 says change failure rate cannot be combined with the other three and forms a factor with rework rate. That concerns change failure rate, not recovery time.) | pp. 11-12 |
| 5 | 2025: AI raises Throughput and hurts Instability | **Verified.** "AI adoption now improves software delivery throughput, a key shift from last year. However, it still increases delivery instability"; "AI is associated with an increase in software delivery instability"; throughput relationship "turned from negative to positive" | DORA 2025 report, pp. 4, 39, 42 |
| 6 | 2025: all seven team profiles | **Verified (closes Gap 5).** Foundational challenges 10%; The legacy bottleneck 11%; Constrained by process 17%; High impact, low cadence 7%; Stable and methodical 15%; Pragmatic performers 20%; Harmonious high-achiever 20%. Shares re-checked in revision 4. The descriptions for profiles 4 and 6 are extraction unclear: quote names and shares only | pp. 15-18 |

## Conflicting Information

### Conflict 1: Set targets for the metrics?
**A**: "ask your teams to set targets for these measures" (*Accelerate*, Ch 2, "Driving Change") [B1]. Management should "set measurable, achievable, time-bound goals for these outcomes" (Ch 4, "What Is Continuous Delivery?") [B1].
**B**: The pitfall "Setting metrics as a goal" [D1]; Finster [P1/V1]; Goodhart [A7].
**Assessment**: Current guidance (B) prevails. The book's very next paragraph warns that in pathological cultures "measurement is used as a form of control". Team-owned improvement goals are not the same as mandated targets.

### Conflict 2: Benchmark and compare teams?
**A**: "We can compare and benchmark teams against the larger organizations they work in and against the wider industry" (*Accelerate*, Ch 2, "Driving Change") [B1]. DORA 2024 provides reference points "relative to their peers" [G4]. The Quick Check compares results with benchmarks derived from the 2025 research [D6].
**B**: The pitfalls "disparate comparisons" and "competing" [D1]; year-over-year beats cross-company comparison [G3]; "the best, most insightful comparisons ... are for the same application or service over time" (DORA 2025 report, p. 20). The 2024 report presents its clusters as "benchmark data" meant "to help inspire all that elite performance is achievable", while saying teams "should focus on improving performance overall" (DORA 2024 report, p. 15).
**Assessment**: DORA does both. Benchmarks are for orientation, not for ranking teams in a league table.

### Conflict 3: Real shift or sampling artefact (2022 no Elite)?
**A**: The pandemic hypothesis [G1]. **B**: "artifacts of sampling and analysis methods" [D6]; snowball sampling [B1 Ch 15]. **Assessment**: Unresolved.

### Conflict 4: Recovery time with stability (2015-2023) or Throughput (2024+)?
This is a definition change across report years [D2]. The site follows 2024+ (GLOSSARY). DORA's 2024 report describes the throughput factor as measuring "the speed of making updates of any kind, normal changes and changes in response to a failure" (DORA 2024 report, p. 12). No statistical test of recovery time's placement appears in the pages read.

### Conflict 5: Does the failure measure move with the others?
**A**: All clusters differ on all four measures; "no tradeoff" [B1 Ch 2], [D1]. **B**: Change fail rate did not correlate in 2014 [D2]; it was excluded from the 2014-2017 construct [B1 App B]; the 2016 inversion [B1 Ch 2]; the 2024 Medium-vs-High inversion; "statistical tests and methods prevent us from combining all four into one factor" (DORA 2024 report, pp. 11, 13). **Assessment**: Both are DORA's own statements. B is the reason DORA itself gives for splitting the factors in 2024.

### Conflict 6: Where does Change Lead Time end?
Ch 2 says "code committed to code successfully running in production". Ch 14, "Surveys Allow You to Collect and Analyze Data Quickly", says "the time from code commit to code in a deployable state". dora.dev says "deployed in production" [D1]. **Use D1.**

### Conflict 7: 2022 overall direction
G1 (2022, re-fetched in revision 2) says High performers were at a "four-year low", Low rose from 7% to 19%, and Medium "swelled to 69% of respondents". The superseded file's phrase "shift toward slightly higher software delivery performance" was not re-confirmed. Use "fewer high performers, no Elite cluster".

### Conflict 8: "Stability" or "Instability" as the 2024 factor name
**A**: The 2024 report names the factor "software delivery stability" (DORA 2024 report, pp. 11-12) and reports AI's effect as a "7.2% reduction" in delivery stability (p. 40).
**B**: The dora.dev history calls it "Software Delivery Instability" [D2]; the metrics guide uses "Instability" [D1]; the 2025 report uses "Software delivery instability" (DORA 2025 report, p. 15) and restates the 2024 AI result as "an estimated 7.2% increase in software delivery instability" (p. 35).
**Assessment**: Same factor, with the label (and so the sign) flipped between the 2024 report and later DORA material. The site follows GLOSSARY ("Instability"). When quoting 2024, keep "stability" inside the quote and note the naming.

### Conflict 9: Foundational challenges (2025): high or low system stability?
**A**: The Google Cloud post says "low performance, high system stability, and high levels of burnout and friction" [G2].
**B**: The 2025 report says "System stability: There are notable challenges with the stability of the software and operational environment" (DORA 2025 report, p. 16).
**Assessment**: The primary report (B) prevails. Do not repeat the blog's "high system stability" description of this profile.

## Knowledge Gaps

1. **Independent replication** of the clusters and the no-trade-off finding. Searched arXiv, ACM, IEEE, Springer and ScienceDirect; none found. Present the finding as DORA's own.
2. **Peer-reviewed methodological critique**. Only untrusted blogs were found, and they were excluded. One claim seen in them (that p < 0.10 was used) is unverified.
3. ~~Why Failed Deployment Recovery Time moved into Throughput~~ **Closed as "description found"** (DORA 2024 report, p. 12). The pages read contain no statistical test of recovery time's placement.
4. ~~2024 report detail~~ **Closed in revision 3** (DORA 2024 report, pp. 11-15). Residual: Figure 1 on p. 14 did not extract cleanly.
5. **Full texts**: the Finster PDF (P1), SPACE (A2), DevEx, CACM "DevOps Metrics" (A1) and A6 were blocked by 403, a login page or a product download.
6. **Finster on measuring individuals**: now found on the product page (a fragment, via the summarising fetch tool); the paper text itself was not read.
7. ~~2025 team profiles~~ **Closed in revision 3** (DORA 2025 report, pp. 15-18). Residual: the descriptions for "High impact, low cadence" and "Pragmatic performers" are interleaved with chart labels; check them against the rendered PDF before quoting.
10. **Page numbering**: citations use the PDF page index from the extraction. On every page checked it matches the printed number, but not every page was checked.
8. **G3 (2023)** was not re-fetched.
9. **Verbatim fidelity of web quotes**: WebFetch summarises and caps quotes at 125 characters. DORA definitions were cross-checked at a pinned commit; P1 fragments were not. Re-check both on the live pages before publishing.

## Doc-writer notes (for a Participant-facing explanation page)

Participants have little prior DORA knowledge. Suggested emphasis:

1. **Lead with the problem.** Start with invisible inventory and the "wall of confusion" (*Accelerate*, Ch 2). Then explain in one sentence each why lines of code, velocity (mark it as the book's example; GLOSSARY says avoid) and utilization fail.
2. **Give the two criteria for a good measure**: a global outcome shared by everyone who delivers, and outcomes rather than output. This sets up why the metrics describe a team and its application or service, never individuals.
3. **Name the groups before the metrics**: Throughput and Instability. Quote DORA's definitions verbatim from Finding 4.1 and credit DORA. Note that GLOSSARY wording differs slightly (table in 4.1). Either align GLOSSARY or quote dora.dev and paraphrase in GLOSSARY terms.
4. **Tell the no-trade-off story honestly.** It is DORA's most memorable finding: Throughput and Instability improve together for most teams and for top performers. Say "the authors propose" small batches and fast feedback as the reason. Add three caveats: the finding comes from survey correlations, not experiments; it has been endorsed but not independently replicated; exceptions exist (2016; 2022; 2024, when DORA named the slower but more stable cluster "medium"; and the 2024 and 2025 AI findings).
5. **Explain "how do they know" in plain words.** Large anonymous surveys since 2014. Questions about concrete practices rather than labels. Groups found by an algorithm with no notion of "good". Results that *predict* organisational performance, which is different from *causing* it.
6. **Be open about limits and sponsorship**: self-selected respondents, Puppet and then Google Cloud as sponsors, and Fowler's caveats in the foreword (quotable, but printed in the programme's own book).
7. **Show a short history**: 2014 four measures; 2023 MTTR becomes Failed Deployment Recovery Time; 2024 Deployment Rework Rate added and Throughput/Instability groups introduced; 2025 team profiles. Mark MTTR, "lead time for changes" and "change failure rate" as historical names.
8. **Make the pitfalls the practical payoff.** Use DORA's seven pitfalls. Support the dashboard and tooling pitfall with Thoughtworks and Huber, and the targets pitfall with Goodhart. Present SPACE and DevEx as related frameworks from the same research community, not as independent confirmation. End with: start with a conversation or the Quick Check, compare with your own past, act on the biggest constraint. This matches the Metric Card prompts.
9. **2024 and 2025 report material can now be used**, always with year and page:
   - The 2024 cluster table (p. 13) and the Medium-vs-High case (p. 14). Present the case as DORA itself explains it. The Medium cluster had lower throughput but better stability than High, yet "This correlation persists even in the medium performance cluster", and "factors besides throughput and stability influence cluster performance". DORA chose to call the faster teams "high". Do not frame it as Throughput and Instability diverging. Note that the 2024 report itself calls the factor "stability" (Conflict 8).
   - The rationale for recovery time in Throughput (p. 12).
   - The seven 2025 profiles (pp. 15-18). Avoid the blog's "high system stability" wording for Foundational challenges (Conflict 9).
   **Avoid** the 2014 market-capitalisation claim and causal wording. Do not use A6 at all. Quote Finster only as attributed in Findings 5.1-5.4 ("P1 product page" fragments, re-checked on the live page, or "as summarised by DX (V1), 2022"). Do not use the 2022 "69%" Medium figure unless you name its year (2022) and source (G1). Do not call the no-trade-off finding "independently endorsed" or "replicated".
10. Use GLOSSARY terms verbatim. In prose say Throughput and Instability, not "speed" or "stability", except inside DORA quotes. Cite the book as "(*Accelerate*, Ch N)". Collect reference-style links at the bottom of the page.

## Full Citations

[B1] Forsgren, N., Humble, J., Kim, G. *Accelerate: The Science of Lean Software and DevOps*. IT Revolution. 2018. Local EPUB. Accessed 2026-10-17.
[B1-F] Fowler, M. "Foreword". In [B1]. 2018.
[D1] Harvey, N. / DORA. "DORA's software delivery performance metrics". dora.dev. 2024-03-29, updated 2026-01-05. https://dora.dev/guides/dora-metrics/ (source: https://raw.githubusercontent.com/dora-team/dora.dev/main/hugo/content/guides/dora-metrics/_index.md). Accessed 2026-10-17.
[D2] Harvey, N. "A history of DORA's software delivery metrics". dora.dev. 2026-01-02. https://dora.dev/guides/dora-metrics/history/. Accessed 2026-10-17.
[D3] DORA. "2024 DORA Report". dora.dev. https://dora.dev/research/2024/dora-report/. Accessed 2026-10-17.
[D4] DORA. "DORA Research: 2024 Questions". dora.dev. https://dora.dev/research/2024/questions/. Accessed 2026-10-17.
[D6] DORA. "Frequently asked questions". dora.dev. Updated 2025-10-06. https://dora.dev/faq/. Accessed 2026-10-17.
[D9] DORA. "DORA 2025: Year in review". dora.dev. https://dora.dev/insights/dora-2025-year-in-review/. Accessed 2026-10-17.
[R24] DORA (Google Cloud). *Accelerate State of DevOps Report 2024* (v. 2024.3). Local file `harness/2024-dora-accelerate-state-of-devops-report.pdf`, read via PDFKit text extraction. Accessed 2026-10-17.
[R25] DORA (Google Cloud). *State of AI-assisted Software Development 2025* (v. 2025.2). Local file `harness/2025_state_of_ai_assisted_software_development.pdf`, read via PDFKit text extraction. Accessed 2026-10-17.
[D8] The DORA Team. "DORA joins Google Cloud". dora.dev. 2018-12-20. https://dora.dev/news/dora-joins-google-cloud/. Accessed 2026-10-17.
[G1] DeBellis, D., Peters, C. "Announcing the 2022 Accelerate State of DevOps Report: A deep dive into security". Google Cloud Blog. 2022-09-29. https://cloud.google.com/blog/products/devops-sre/dora-2022-accelerate-state-of-devops-report-now-out/. Accessed 2026-10-17.
[G2] Harvey, N., DeBellis, D. "Announcing the 2025 DORA Report: State of AI-Assisted Software Development". Google Cloud Blog. 2025-09-23. https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report. Accessed 2026-10-17.
[G3] DeBellis, D., Harvey, N. "2023 State of DevOps Report: Culture is everything". Google Cloud Blog. 2023-10-05. https://cloud.google.com/blog/products/devops-sre/announcing-the-2023-state-of-devops-report. Accessed 2026-10-17 (prior run).
[G4] Harvey, N., DeBellis, D. "Highlights from the 10th DORA report". Google Cloud Blog. 2024-10-23. https://cloud.google.com/blog/products/devops-sre/announcing-the-2024-dora-report. Accessed 2026-10-17.
[P1] Finster, B. "How to Misuse & Abuse DORA Metrics". IT Revolution guidance paper; DevOps Enterprise Journal, Spring 2022. May 2022. https://itrevolution.com/product/how-to-misuse-abuse-dora-metrics/. Accessed 2026-10-17 (product page only).
[A1] Forsgren, N., Kersten, M. "DevOps Metrics". *Communications of the ACM* 61(4). 2018. https://queue.acm.org/detail.cfm?id=3182626. [Restricted Access].
[A2] Forsgren, N., Storey, M.-A., Maddila, C., Zimmermann, T., Houck, B., Butler, J. "The SPACE of Developer Productivity". ACM Queue 19(1). 2021. https://queue.acm.org/detail.cfm?id=3454124. [Restricted Access; via I1].
[A5] Sánchez Ruiz, J. M., Domínguez Mayo, F. J., Oriol, X., Crespo, J. F., Benavides, D., Teniente, E. "A Benchmarking Proposal for DevOps Practices on Open Source Software Projects". arXiv:2304.14790. 2023. https://arxiv.org/abs/2304.14790. Accessed 2026-10-17.
[A6] Authors unknown. "Fully Automated DORA Metrics Measurement for Continuous Improvement". ACM, ICSSP 2024. doi:10.1145/3666015.3666020. [Unverified search extract].
[A7] Manheim, D., Garrabrant, S. "Categorizing Variants of Goodhart's Law". arXiv:1803.04585. 2018. https://arxiv.org/abs/1803.04585. Accessed 2026-10-17.
[I1] De Simone, S. "SPACE, a New Framework to Understand and Measure Developer Productivity". InfoQ. 2021-03-18. https://www.infoq.com/news/2021/03/space-developer-productivity. Accessed 2026-10-17.
[I2] Linders, B. "Experiences from Measuring the DevOps Four Key Metrics: Identifying Areas for Improvement" (reporting Nikolaus Huber, Reservix, DevOpsCon Berlin 2021). InfoQ. 2021-08-12. https://www.infoq.com/news/2021/08/measuring-four-key-metrics/. Accessed 2026-10-17.
[I3] Noda, A. "DevEx, a New Metrics Framework from the Authors of SPACE". InfoQ. 2023-05-16. https://www.infoq.com/articles/devex-metrics-framework/. Accessed 2026-10-17.
[I4] InfoQ. "Dr. Nicole Forsgren on the DORA & Google Collaboration on the New Accelerate State of DevOps Report". 2018-04. https://www.infoq.com/news/2018/04/DORA-Google-Cloud-New-Research/. [Search extract only].
[F1] Fowler, M. "Cannot Measure Productivity". martinfowler.com. 2003-08-29. https://martinfowler.com/bliki/CannotMeasureProductivity.html. Accessed 2026-10-17.
[T1] Thoughtworks. "DORA metrics". Technology Radar, Nov 2018 to Apr 2026. https://www.thoughtworks.com/en-gb/radar/techniques/dora-metrics. Accessed 2026-10-17.
[V1] Noda, A. "How to Misuse & Abuse DORA Metrics" (summary of P1). Engineering Enablement newsletter (DX). 2022-07-22. https://newsletter.getdx.com/p/misuse-dora. Accessed 2026-10-17. [Vendor]
[V2] Pearson, B. L. "What are DORA Metrics and How to Unlock Elite Engineering Performance". LinearB. 2024-08-22, updated 2025-04-08. https://linearb.io/blog/dora-metrics. Accessed 2026-10-17. [Vendor]

## Research Metadata
Revision 4 (2026-10-17): Q1 (recovery-time wording), Q2 (PDF provenance) and notes N1-N4 applied. Revision 3: cited 29 (R24 and R25 read through the coordinator's PDFKit text extraction; D9 added in revision 2; X1 removed in revision 1). Earlier tool failures: the PDFs could not be rendered (`pdftoppm` missing); the web fetch of the 2024 PDF exceeded 10 MB; ACM returned 403; Springer redirected to a login page; the Finster PDF is a product download; WebFetch caps quotes at 125 characters (definitions were reassembled from head and tail fetches of the raw source). Output: docs/research/measuring-software-delivery-performance-for-explanation-doc.md

## Research Review
research_review: iteration 3, verdict NEEDS_REVISION, blocking Q1 and Q2; reviewer condition "approvable without another pass once Q1 and Q2 are applied".
Q1 and Q2 applied in revision 4 (2026-10-17).
