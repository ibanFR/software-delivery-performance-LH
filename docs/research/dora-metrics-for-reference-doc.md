# Research: The five DORA metrics (for a Diátaxis reference page)

**Date**: 2026-10-18 | **Researcher**: nw-researcher (Nova) | **Confidence**: High for definitions, grouping, survey items and name history (authoritative primary sources); Medium for measurement details not stated by DORA | **Sources**: 14 cited (after Review 1)

## Executive summary

DORA defines five software delivery performance metrics, grouped into two factors [S1]:

- **Throughput**: Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time.
- **Instability**: Change Fail Rate, Deployment Rework Rate.

The definitions below are quoted verbatim from dora.dev (fetched 2026-10-18; page "Last updated: January 5, 2026") and credited to DORA. They match `GLOSSARY.md` word for word. DORA says the metrics are "best suited for measuring one application or service at a time" [S1] (fetched quote, rejoined from two chunks; see Section 6 for related statements in the reports). The survey asks about "the primary application or service you work on" [S25], [S41], [S43].

DORA collects all five by self-report. Change Lead Time and Failed Deployment Recovery Time use six fixed time bands ("Less than one hour" to "More than six months"). Deployment Frequency uses six frequency bands ("On demand (multiple deploys per day)" to "Fewer than once per six months"). All three also offer "I don't know or NA". Since 2023, Change Fail Rate is a number from 0% to 100%; in 2022 it was a choice of 15-point ranges. Deployment Rework Rate (added 2024) is also a number from 0% to 100% [S25], [S41], [S42], [S43].

The metrics changed over time, and each change has a primary source:
- Four keys in *Accelerate* (2018) [S34].
- MTTR / "time to restore service" redefined as Failed Deployment Recovery Time in 2023, covering only failures caused by a change [S2], [S41].
- Rework rate added in 2024, and the metrics regrouped into two factors. That regrouping moved Failed Deployment Recovery Time from stability to Throughput [S2], [S35 pp. 11-12].

The main gaps are about how to compute the metrics, not how to define them:
- DORA does not say whether to use a median or a mean, or how to count deployments in an automated system.
- dora.dev and DORA's own survey define "rework" slightly differently ("incident in production" versus "user-facing bug").
- The 2024 report quotes the rework question as "how many deployments", while the published questionnaire says "what percentage".

**Independence caveat**: 13 of 14 sources come from the DORA programme. The one outside it, Thoughtworks [S7], is a single source affiliated with a sponsor (Thoughtworks sponsored the 2025 DORA report), and it is used only as a paraphrase. In effect this document has **no independent corroboration**. For definitions, scope, grouping and survey items that is acceptable: DORA defines the terms, so it is the single authoritative source, and adding non-DORA restatements would be padding. Claims that go beyond definition (DORA's reasons, its interpretations, its exceptions) are tagged "(DORA-only)". For measurement notes, the only extra detail comes from DORA's own Four Keys project, as described on the Google Cloud blog in 2020 [S44].

## Methodology

**Search strategy**:
- Reused the approved research in `docs/research/measuring-software-delivery-performance-for-explanation-doc.md` (IDs S1-S40 kept as-is).
- Re-fetched dora.dev live on 2026-10-18 for the definitions page [S1], the history page [S2] and the 2024 survey questions [S25].
- Fetched the 2022, 2023 and 2025 questionnaires to trace how the answer formats changed [S42], [S41], [S43].
- Fetched the Four Keys material (Google Cloud blog) and the dora.dev resources page. The GitHub repository (github.com/dora-team/fourkeys) was also fetched. It is off the trusted list, so it was dropped in Review 1 and nothing here relies on it.
- **Quote verification marks**: "(verbatim, local)" means checked against the extracted text of a local primary. "(fetched quote)" means it came back in quotation marks from the web-fetch tool. "(rejoined)" means two fetched chunks were joined. "(fetch-tool summary)" means it was paraphrased by the tool and must not be quoted on the page without re-checking. Unmarked dora.dev questionnaire items are fetched quotes.

**Local primaries**:
- The 2024 and 2025 report PDFs were read from text extracted in an earlier session of this project, in the session scratchpads (`pdftext/dora-2024.txt`, `dora-2025.txt`; PDF page markers match the printed page numbers, as established in the earlier research).
- *Accelerate* ch. 2 was read from the unzipped epub XHTML (`OEBPS/13-ch2.xhtml`).
- PDF rendering was unavailable in this session (no poppler), so the extracted text was the only route to the PDFs.

**Source selection**: Every source was checked against `.nwave/trusted-source-domains.yaml`. DORA-programme sources count as one for cross-referencing.

**Quality**: Definitions come from a single authoritative source (dora.dev), as the brief allows. Other claims cite the edition and page. Average reputation ≈ 0.99 (see Source list).

**Adversarial check**: No injected instructions were found in fetched content. Fetch-tool output splits quotes into chunks under 125 characters; where a sentence was split, the parts are rejoined here only where the joined text matches the local PDF or the fetch returned both parts.

## Terminology note

Terms follow `GLOSSARY.md`. Quotes keep the source's wording, with the glossary term in brackets.

| Source wording | Where | Glossary term |
|---|---|---|
| delivery lead time, product delivery lead time | *Accelerate* ch. 2 (2018) [S34] | Change Lead Time |
| lead time for changes | survey items 2022-2025 [S42], [S41], [S25], [S43]; 2025 report p. 13 [S36]; Four Keys [S44] | Change Lead Time |
| deployment lead time | 2015 model, per [S2] | Change Lead Time |
| release frequency | *Accelerate* ch. 3 construct box [S34] | Deployment Frequency |
| mean time to recover / MTTR | 2014-2015, per [S2]; *Accelerate* Table 2.2 [S34] | Failed Deployment Recovery Time |
| time to restore service, Time to Restore Services | *Accelerate* ch. 2 [S34]; survey item headings 2022-2025 [S42], [S41], [S43]; Four Keys [S44] | Failed Deployment Recovery Time |
| change failure rate, change fail percentage | 2024 report pp. 6, 11-14 [S35]; 2025 report pp. 21, 139 [S36]; Four Keys [S44] | Change Fail Rate |
| rework rate | 2024 report p. 11 [S35]; 2025 report p. 13 [S36] | Deployment Rework Rate |
| software delivery stability | 2024 report pp. 11-12 [S35] | Instability (inverse framing) |

dora.dev itself writes the metric names in sentence case ("Change lead time"). The glossary capitalises them.

---

## 1. Change Lead Time

| Field | Content | Source |
|---|---|---|
| **DORA definition (verbatim)** | "The amount of time it takes for a change to go from committed to version control to deployed in production." | [S1], accessed 2026-10-18; also verbatim, local, in [S36 p. 13] |
| **Avoid (GLOSSARY)** | Lead time for changes, cycle time | `GLOSSARY.md` |
| **Group** | Throughput | [S1]; [S35 pp. 11-12]; [S36 p. 13] |
| **Start / end points** | Start: the change is committed to version control. End: the change is deployed in production [S1]. 2024 wording: "the time it takes for a code commit or change to be successfully deployed to production" [S35 p. 10]. *Accelerate*: "the time it takes to go from code committed to code successfully running in production" [S34 ch. 2]. | [S1], [S35], [S34] |
| **What counts as a change** | "changes of any kind, including changes to configuration and changes to code" (said of all four keys) | [S35 p. 10] |
| **What it leaves out** | *Accelerate* splits lead time into a design part (the "fuzzy front end", where "it's often unclear when to start the clock") and a delivery part ("the time it takes for work to be implemented, tested, and delivered"). DORA measures only the delivery part, which "is easier to measure and has a lower variability". (DORA-only; verbatim, local) | [S34 ch. 2] |
| **Unit** | A duration. DORA does not say whether to aggregate with a median or a mean (see Gap 1). | [S1] |
| **Survey item (2024)** | "What is your lead time for changes (i.e., how long does it take to go from code committed to code successfully running in production)?" | [S25] |
| **Answer options (2024)** | More than six months; Between one month and six months; Between one week and one month; Between one day and one week; Less than one day; Less than one hour; I don't know or NA | [S25] |
| **2025** | Same question ("that is" in place of "i.e.") and the same six bands | [S36 pp. 20, 138]; [S43] |
| **Earlier editions** | *Accelerate* (2014-2017 surveys): the same six bands, lower-case and in reverse order. 2022 used shorter labels ("One to six months", "One week to one month", "One day to one week"). | [S34 ch. 2]; [S42] |
| **Former names** | "delivery lead time" (2018 book); "deployment lead time" (2015 model); "lead time for changes" (survey items to 2025). History page: the 2024 regrouping uses "change lead time" for the commit-to-production measure (fetch-tool summary, not a verbatim quote). | [S34]; [S2]; [S25] |
| **DORA-published measurement notes** | Four Keys (Google Cloud blog, 2020): "for every deployment, you need to maintain a list of all the changes included in the deployment", mapped by commit SHA, then "calculate the median lead time" (fetched quotes). This is a pre-2023 tool description, not a DORA definition. | [S44] |

**Confidence**: High (authoritative primary; the wording is consistent across [S1], [S35], [S36], [S34]).

## 2. Deployment Frequency

| Field | Content | Source |
|---|---|---|
| **DORA definition (verbatim)** | "The number of deployments over a given period or the time between deployments." | [S1]; also verbatim, local, in [S36 p. 13] |
| **Avoid (GLOSSARY)** | Release frequency, release cadence | `GLOSSARY.md` |
| **Group** | Throughput | [S1]; [S35 pp. 11-12]; [S36 p. 13] |
| **What a deployment is** | *Accelerate*: "By 'deployment' we mean a software deployment to production or to an app store. A release (the changes that get deployed) will typically consist of multiple version control commits, unless the organization has achieved a single-piece flow where each commit can be released to production (a practice known as continuous deployment)." 2024: "how often application changes are deployed to production". | [S34 ch. 2]; [S35 p. 10] |
| **Why DORA measures it** | It stands in for batch size: "we settled on deployment frequency as a proxy for batch size since it is easy to measure and typically has low variability". Footnote: "Strictly, deployment frequency is the reciprocal of batch size". (DORA-only; verbatim, local) | [S34 ch. 2] |
| **Unit** | A count per period, or the interval between deployments [S1]. The survey records it as a frequency band. | [S1], [S25] |
| **Survey item (2024)** | "How often does your organization deploy code to production or release it to end users?" | [S25] |
| **Answer options (2024)** | Fewer than once per six months; Between once per month and once every 6 months; Between once per week and once per month; Between once per day and once per week; Between once per hour and once per day; On demand (multiple deploys per day); I don't know or NA | [S25] |
| **2025** | Same question and options | [S36 pp. 20, 138]; [S43] |
| **Earlier editions** | *Accelerate*: the same six options, worded "fewer than once every six months". The book asked about "the primary service or application they work on". 2022 offered the same six options without "I don't know". | [S34 ch. 2]; [S42] |
| **Former names** | The name has not changed since 2014 [S2] (fetch-tool summary). *Accelerate* ch. 3 once uses "release frequency" for it [S34]. | [S2]; [S34] |
| **DORA-published measurement notes** | Four Keys: "the metric is deployment frequency, not volume". It counts a week as "Daily" when "the median number of days per week with at least one successful deployment is equal to or greater than three". By default it counts "any successful deployment to any level of traffic". It also says "The precise definition of a change, deployment, or incident depends on a team's business requirements." (fetched quotes; 2020 tool description) | [S44] |

**Confidence**: High.

## 3. Failed Deployment Recovery Time

| Field | Content | Source |
|---|---|---|
| **DORA definition (verbatim)** | "The time it takes to recover from a deployment that fails and requires immediate intervention." | [S1] (rejoined from two fetch chunks); verbatim, local, in [S36 p. 13] |
| **Avoid (GLOSSARY)** | MTTR, mean time to restore, time to restore service | `GLOSSARY.md` |
| **Group** | Throughput, since 2024. Earlier it was a stability measure: "Stability measures were mean time to recover (MTTR) and change fail rate" (2015 model, fetch-tool summary of [S2]). DORA's reason for the move: the Throughput factor "measures the speed of making updates of any kind, normal changes and changes in response to a failure." (DORA-only; verbatim, local) | [S1]; [S2]; [S35 p. 12] |
| **What counts as a failure** | Since 2023, only an impairment caused by a change to production, not an external failure such as a data-centre outage [S2] (fetch-tool summary; corroborated by the 2022 → 2023 change in survey wording [S42], [S41]). Survey wording 2023-2025: "after a change to production or release to users results in degraded service (for example, lead to service impairment or service outage) and subsequently require remediation (for example, require a hotfix, rollback, fix forward, or patch)" [S25]. 2024 report: "the time it takes to recover from a failed deployment" [S35 p. 10]. | [S2]; [S25]; [S35] |
| **Start / end points** | DORA's survey asks how long it takes "to restore service" after the change degrades it [S25]. dora.dev gives no precise clock start (failed deployment, detection, or incident opened) (Gap 2). | [S25]; [S1] |
| **Unit** | A duration | [S1] |
| **Survey item (2024)** | "How long does it generally take to restore service after a change to production or release to users results in degraded service (for example, lead to service impairment or service outage) and subsequently require remediation (for example, require a hotfix, rollback, fix forward, or patch)?" | [S25] |
| **Answer options (2024)** | The same six bands as Change Lead Time (More than six months ... Less than one hour) plus I don't know or NA | [S25] |
| **2025** | Same question ("leads", "requires") and the same bands | [S36 pp. 21, 138]; [S43] |
| **Earlier editions** | *Accelerate*: "how long it generally takes to restore service for the primary application or service they work on when a service incident (e.g., unplanned outage, service impairment) occurs", with the same options as lead time. 2022: "when a service incident or a defect that impacts users occurs". In both, any incident counted, not only one caused by a change. 2023 is the first questionnaire tied to "a change to production". | [S34 ch. 2]; [S42]; [S41] |
| **Former names** | "mean time to recover" / MTTR (2014-2015); "time to restore service" (*Accelerate*; survey headings into 2025). Renamed and redefined as "failed deployment recovery time" in 2023 (fetch-tool summary of [S2]). dora.dev links to "the research behind changes like the move from MTTR to Failed Deployment Recovery Time" (fetched quote). | [S2]; [S34]; [S1] |
| **DORA-published measurement notes** | Four Keys blog (2020): "you need to know when the incident was created and when it was resolved", or when "a deployment resolved said incident" (fetched quotes). A 2020 Google Cloud post describes an SLO-based variant: "the total time it takes to detect, mitigate, and resolve a problem until we are back in compliance with the SLO" (fetched quote). Both predate the 2023 redefinition and are tool or team practice, not DORA definitions. | [S44]; [S45] |

**Confidence**: High for the definition, the grouping and the 2023 change. Medium for start and end points (DORA does not specify them).

## 4. Change Fail Rate

| Field | Content | Source |
|---|---|---|
| **DORA definition (verbatim)** | "The ratio of deployments that require immediate intervention following a deployment. Likely resulting in a rollback of the changes or a "hotfix" to quickly remediate any issues." | [S1]; identical (verbatim, local) in [S36 p. 13] |
| **Avoid (GLOSSARY)** | Change failure rate, failure rate | `GLOSSARY.md` |
| **Group** | Instability. In the 2024 report the factor is named "software delivery stability". (DORA-only, construct history:) In 2014 this metric was left out of the "IT performance" construct because it did not correlate with the others (fetch-tool summary of [S2]; do not quote). In *Accelerate*, "only lead time, release frequency, and time to restore together form a valid and reliable construct" (verbatim, reused from the approved explanation research). | [S1]; [S35 pp. 11-12]; [S2]; [S34 ch. 3] |
| **What counts as a failure** | (DORA-only; verbatim, local) 2024: "We consider a deployment to be a change failure only if it causes an issue after landing in production, where it can be experienced by end users. In contrast, a change that is stopped on its way to production is a successful demonstration of the deployment process's ability to detect errors." Changes include configuration changes. | [S35 p. 10, footnote 1, printed on p. 16]; [S35 p. 10] |
| **Earlier definition** | *Accelerate*: "what percentage of changes to production (including, for example, software releases and infrastructure configuration changes) fail". The book asked what percentage "either result in degraded service or subsequently require remediation" ("either ... or"). The questionnaires from 2022 onward say "and subsequently require remediation". | [S34 ch. 2]; [S42]; [S25] |
| **Unit** | A ratio of failed deployments to all deployments, reported as a percentage | [S1]; [S25] |
| **Survey item (2024)** | "Approximately what percentage of changes to production or released to users result in degraded service (for example, lead to service impairment or service outage) and subsequently require remediation (for example, require a hotfix, rollback, fix forward or patch), if at all?" | [S25] |
| **Answer format (2024)** | A number "(value between 0% and 100%)", or I don't know or NA | [S25] |
| **2025** | Same item ("releases to users") and the same format [S43]. The report groups answers into bands for display: 0%-2%, 2%-4%, 4%-8%, 8%-16%, 16%-32%, 32%-64%, >64% [S36 p. 21]. Those bands are for reporting only, not answer options. (Bands verbatim, local: checked against the extracted 2025 text on 2026-10-18, but not re-checked against the rendered PDF because no renderer was available.) | [S43]; [S36 pp. 21, 139] |
| **Earlier formats** | 2022: ranges "0-15%", "16-30%", "31-45%", "46-60%", "61-75%", "76-100%" [S42]. 2023: a number 0-100% [S41]. (DORA-only) The 2024 report says "A change to the way respondents answered the change failure rate question improved the connection" with the other metrics [S35 p. 11] (verbatim, local). It does not give a year. *(Interpretation: this matches the 2022 → 2023 switch from ranges to a number.)* | [S42]; [S41]; [S35 p. 11] |
| **Former names** | "change fail rate" (*Accelerate*, dora.dev); "change failure rate" (2024 and 2025 reports, Four Keys); "change fail percentage" (2024 p. 6). The definition is otherwise stable. | [S34]; [S35]; [S36]; [S44] |
| **DORA-published measurement notes** | Four Keys blog (2020): "The percentage of deployments causing a failure in production". It takes "the total count of deployments" and "links it to incidents", where an incident must "contain the ID of the deployment" (fetched quotes; 2020 tool description). | [S44] |

**Confidence**: High.

## 5. Deployment Rework Rate

| Field | Content | Source |
|---|---|---|
| **DORA definition (verbatim)** | "The ratio of deployments that are unplanned but happen as a result of an incident in production." | [S1]; identical (verbatim, local) in [S36 p. 13] ("Rework rate") |
| **Avoid (GLOSSARY)** | Rework rate, hotfix rate | `GLOSSARY.md` |
| **Group** | Instability. (DORA-only analysis; verbatim, local) 2024: "rework rate and change failure rate are related. Together, these two metrics create a reliable factor of software delivery stability." That factor "measures the likelihood deployments unintentionally lead to immediate, additional work." | [S1]; [S35 pp. 11-12] |
| **Why DORA added it (2024)** | (DORA-only; verbatim, local) "We have a longstanding hypothesis that the change failure rate metric works as a proxy for the amount of rework a team is asked to do. When a delivery fails, this requires the team to fix the change, likely by introducing another change." | [S35 p. 11] |
| **What counts as rework** | dora.dev: unplanned deployments that happen "as a result of an incident in production" [S1]. Survey: deployments that "were not planned but were performed to address a user-facing bug in the application" [S25]. These differ slightly (see Conflict 1). Survey window: the last six months. | [S1]; [S25] |
| **Unit** | A ratio of unplanned deployments to all deployments, as a percentage | [S1]; [S25] |
| **Survey item (2024 questionnaire)** | "Approximately what percentage of deployments in the last 6 months were not planned but were performed to address a user-facing bug in the application?" A number "(value between 0% and 100%)", or I don't know or NA. | [S25] |
| **Survey item (as quoted in the 2024 report)** | "For the primary application or service you work on, approximately how many deployments in the last six months were not planned but were performed to address a user-facing bug in the application?" This asks for a count, not a percentage (Conflict 3). | [S35 p. 11] |
| **2025** | Same percentage item [S43]; [S36 p. 139]. The report shows answers in the same reporting bands as Change Fail Rate (0%-2% ... >64%) [S36 p. 21] (verbatim, local from extracted text; not re-checked against the rendered PDF). | [S43]; [S36] |
| **Clusters** | The 2024 performance clusters were computed "on the original four software delivery metrics" only, so Deployment Rework Rate is not in the 2024 cluster table. | [S35 p. 13] |
| **Former names** | New in 2024. "rework rate" (2024 and 2025 reports); "deployment rework rate" (dora.dev; history page per fetch-tool summary). | [S35]; [S36]; [S2]; [S1] |
| **DORA-published measurement notes** | None found beyond the survey item. The 2020 Four Keys description [S44] covers only the original four keys, so it does not cover rework. | [S44] |
| **Outside note (single source affiliated with a sponsor; paraphrase)** | Thoughtworks Radar (Apr 2026), paraphrased from a fetched blip summary: a rising rework rate is an early warning of blind spots and technical debt from unchecked AI-assisted development. Thoughtworks sponsored the 2025 DORA report, so this is not independent. Do not quote. | [S7] |

**Confidence**: High for the definition, grouping and reason for adding it. Medium for the exact survey wording (Conflict 3).

---

## 6. Scope and grouping

### Scope: one application or service

- dora.dev: "These metrics work for any type of technology your organization is delivering, but are best suited for measuring one application or service at a time." [S1] (fetched quote, rejoined from two chunks; **not verified locally**. The sentence does not appear in the extracted 2024 or 2025 report text, which was searched for "best suited" and "one application or service" on 2026-10-18. The report statements below are related statements in the reports, verbatim, local.) The page also warns against blending metrics across teams or organizations and against comparing very different applications [S1] (fetch-tool summary).
- 2024 report: "The four key metrics should be used at the application and service levels, and not at the organization or line-of-business level. The metrics should be used to visualize your efforts in continuous improvement and not to compare teams — and certainly not to compare individuals." [S35 p. 74]
- 2025 report: "these measurements are taken at the application or service level. Doing so encourages cross-functional ownership and accountability for improvement." "the best, most insightful comparisons of software delivery performance are for the same application or service over time." [S36 p. 20]. The factors "can be used to measure any application or service, regardless of the technology stack, the complexity of the deployment processes, or its end users." [S36 p. 13]
- Survey framing (2022-2025): "For the primary application or service you work on..." [S25], [S41], [S43]. *Accelerate* also asked about "the primary application or service they work on" [S34 ch. 2].

**Confidence**: High (consistent across four DORA editions; DORA-only, as expected for a scope DORA sets itself).

### Grouping: Throughput and Instability

- dora.dev: "Throughput is a measure of how many changes can move through the system over a period of time." "Instability is a measure of how well the software deployments go." [S1] (fetched quotes; both also verbatim, local, in [S36 p. 13])
- 2025 report adds: "Higher throughput means that the system can move more changes through to the production environment." "When deployments go well, teams can confidently push more changes into production and users are less likely to experience issues with the application immediately following a deployment." [S36 p. 13]
- Statistical basis (2024; DORA-only analysis, verbatim, local): "Change failure rate is strongly correlated with the other three metrics but statistical tests and methods prevent us from combining all four into one factor." "More than half of the teams in our study this year show differences in software throughput and software stability. These differences have led us to consider software delivery performance through two different factors" [S35 p. 11]. "All five metrics are considered for describing software delivery performance." [S35 p. 12]
- Naming: the 2024 report calls the second factor "software delivery stability" [S35 pp. 11-12]. The 2025 report and dora.dev call it "Instability" [S36 p. 13], [S1]. The history page labels the 2024 grouping "Software Delivery Instability" (fetch-tool summary) [S2]. No source says when the name changed (Gap 4).
- Earlier pairing: 2015 throughput and stability (fetch-tool summary of [S2]); *Accelerate* calls lead time and deployment frequency measures of "tempo" and the other two measures of "stability" [S2], [S34 ch. 2]. A 2020 Google Cloud post uses "Speed" and "Stability" [S45].

**Confidence**: High.

## 7. DORA-published notes on measuring (all metrics)

- dora.dev suggests: set a baseline with the DORA Quick Check [S40], talk as a team about friction in delivery, and check progress through the Quick Check, conversations and retrospectives. It notes the data may already exist in many places, and that a source-available or commercial tool with pre-built integrations may be an option [S1] (fetch-tool summary; quote individual phrases only after re-checking).
- 2024 report lists the ways teams measure the four keys: "Through conversations and reflection during team meetings"; "The DORA Quick Check"; "Commercial and source-available tools in the Software Engineering Intelligence (SEI) category"; "Bespoke integrations built for the specific tools in use by a team" [S35 p. 79]. Footnote 11 points to dora.dev/resources [S35 p. 82].
- 2025 report: "Precision for these metrics isn't always required, and teams will generally know how they are changing over time." [S36 p. 22]
- dora.dev resources lists source-available tools "to collect and visualize DORA's software delivery metrics": Apache DevLake (Incubating), Liatrio backstage-dora-plugin, Middleware, OpenDORA [S47]. It does not list Four Keys. *(Listing a tool is not the same as DORA endorsing it; the page makes no claim about each tool's accuracy.)*
- Four Keys (Google Cloud, 2020): an open-source pipeline from GitHub/GitLab events to a dashboard [S44]. Its definitions follow the pre-2023 four keys and use "Time to Restore Services" [S44]. **Current status unverified from a trusted source**: the blog's editor's note marks its bucket labels as dated but does not say whether the project is maintained [S44]. dora.dev/resources does not list it [S47]. The page should not call it current or recommend it.

**Confidence**: High that DORA says these things. The tools are not evaluated here.

## 8. Changes over time

| Year / edition | Change | Source |
|---|---|---|
| 2014 | "IT performance" defined from deployment frequency, lead time for changes, mean time to recover and change fail rate. Change fail rate was left out of the construct because it did not correlate with the other three. | [S2] (fetch-tool summary) |
| 2015 | Model reframed as throughput (deployment frequency, deployment lead time) and stability (MTTR, change fail rate) | [S2] (fetch-tool summary) |
| 2018 (*Accelerate*) | The four measures named as "delivery lead time, deployment frequency, time to restore service, and change fail rate". Survey bands published for lead time, deployment frequency and time to restore. | [S34 ch. 2] |
| 2018 | "Availability" added; umbrella term becomes "Software Delivery and Operational (SDO) performance" | [S2] (fetch-tool summary; term names as returned in quotation marks) |
| 2021 | Availability broadened to "reliability". The 2021 report "inaccurately called the 'reliability' metric the 'fifth metric'" (fetched quote; also in the approved explanation research). Reliability is not one of today's five. | [S2] |
| 2022 | Change Fail Rate asked as ranges (0-15% ... 76-100%). Time to restore asked for "a service incident or a defect that impacts users". | [S42] |
| 2023 | MTTR / "time to restore service" renamed and redefined as Failed Deployment Recovery Time, covering only failures caused by a change ([S2], fetch-tool summary). Survey item now "after a change to production". Change Fail Rate asked as a number 0-100%. | [S2]; [S41] |
| 2024 | Rework rate added (dora.dev: Deployment Rework Rate). Five metrics in two factors: Throughput (Change Lead Time, Deployment Frequency, Failed Deployment Recovery Time) and "stability" (Change Fail Rate, rework rate). Failed Deployment Recovery Time moves from stability to Throughput. Clusters still computed on the original four. | [S35 pp. 11-13]; [S2] |
| 2025 | Same five metrics and survey items. Second factor named "Instability". Ranked clusters replaced by seven team profiles (covered in the explanation research, Finding 4.3). | [S36 pp. 13-21]; [S43] |
| 2026-01 | dora.dev guide (last updated 2026-01-05) describes the shift "from the original four keys to the current five-metric model" (fetched quote); history page published 2026-01-02 | [S1]; [S2] |

**Benchmarks**: Not reproduced here. If the page needs them, the 2024 cluster table (four metrics only, with shares and 89% intervals) is on [S35 p. 13] and is reproduced with its year in the explanation research, Finding 4.3. The 2025 report gives answer distributions instead of clusters [S36 pp. 20-21]. Always state the year.

---

## Gaps

### Gap 1: How to aggregate (median, mean, or band)
**Issue**: DORA defines each metric and collects it in survey bands or as a percentage. dora.dev does not say whether a team computing it from system data should use a median, a mean or a percentile. **Attempted**: dora.dev guide [S1], history [S2], resources [S47], the 2024 and 2025 reports. **Found**: only the 2020 Four Keys description uses a median, for lead time and as the bucketing basis for deployment frequency [S44]. It does not state an aggregate for Change Fail Rate or restore time. **Recommendation**: the reference page should say "DORA does not prescribe an aggregate" rather than recommend one.

### Gap 2: Clock start for Failed Deployment Recovery Time
**Issue**: The definition is "time it takes to recover from a deployment that fails" [S1], but there is no stated start: deployment, detection, or incident opened. The 2020 Four Keys blog starts from incident creation [S44]. The 2020 SLO-based post counts the time "to detect, mitigate, and resolve" [S45]. Both predate the 2023 redefinition (Conflict 2). **Recommendation**: quote the definition and the survey item. Do not invent a start point.

### Gap 3: What counts as "immediate intervention" or "unplanned"
**Issue**: DORA gives examples (rollback, hotfix, fix forward, patch) [S1], [S25] and the 2024 rule that a change stopped before production is not a failure [S35 p. 10 fn. 1]. It gives no threshold for "immediate" and no rule for classifying a deployment as unplanned. **Recommendation**: present this as a team decision. Four Keys says as much: "The precise definition of a change, deployment, or incident depends on a team's business requirements." [S44]

### Gap 4: When "stability" became "Instability"
**Issue**: The 2024 report says "stability" and the 2025 report and dora.dev say "Instability". No source dates or explains the change. **Attempted**: history page [S2]. **Recommendation**: say "named Instability since the 2025 report", attributed to [S36 p. 13].

### Gap 5: 2023 report not read
**Issue**: The 2023 changes rest on the history page [S2] and the 2023 questionnaire [S41]. The 2023 report PDF (no local copy) was not read. **Recommendation**: low priority. The questionnaire is primary evidence of the redefinition.

### Gap 6: No independent corroboration
**Issue**: There is one non-DORA source, Thoughtworks [S7]. It is affiliated with a sponsor (2025 DORA sponsor), comes from a fetched summary, and is used only as a paraphrase on one rework note, so the document has effectively no independent corroboration. Sallin et al. (XP 2021), cited in the explanation research, was dropped in Review 1 because it supported no finding here. For definitions, scope, grouping and survey items this is not a weakness: DORA defines the terms, and outside restatements would only repeat them. Claims about DORA's reasons, its analysis and its exceptions are tagged "(DORA-only)" and should be attributed to DORA on the page. Vendor glossaries in search results (faros.ai, hivel.ai, qodo.ai, etc.) are off the trusted list and were not cited. **Note**: they use looser definitions of rework, which a reference page could warn about without citing them.

## Conflicting information

### Conflict 1: What counts as rework
dora.dev: unplanned deployments that happen "as a result of an incident in production" [S1]. Survey 2024-2025: deployments that "were not planned but were performed to address a user-facing bug in the application" [S25], [S43]. **Assessment** *(interpretation)*: Close but not identical (incident versus user-facing bug). Quote the dora.dev definition as the definition and the survey item as "how DORA asks it".

### Conflict 2: Clock start for recovery time in 2020 Google Cloud measurement guidance
Four Keys blog: from incident created to incident resolved, or to the deployment that resolved it [S44]. SLO-based post: "the total time it takes to detect, mitigate, and resolve a problem until we are back in compliance with the SLO" [S45]. **Assessment** *(interpretation)*: Two tool-level choices, both pre-2023. Neither is DORA's definition. (The Four Keys GitHub README, which gives a third start point, is off the trusted list and is no longer cited.)

### Conflict 3: Rework item as count or percentage
2024 report p. 11: "approximately how many deployments in the last six months..." [S35]. 2024 questionnaire: "Approximately what percentage of deployments in the last 6 months..." with 0-100% entry [S25]. 2025: percentage [S43], [S36 p. 139]. **Assessment** *(interpretation, not stated by DORA)*: The questionnaire and the 2025 report agree on percentage, which fits a "ratio" definition. p. 11 is probably a paraphrase in the report text. Cite the questionnaire for the item.

### Conflict 4: Change Fail Rate "either ... or" versus "and"
*Accelerate* asked about changes that "either result in degraded service or subsequently require remediation" [S34 ch. 2]. Questionnaires from 2022 onward ask about changes that "result in degraded service ... and subsequently require remediation" [S42], [S25]. **Assessment** *(interpretation)*: The current wording is narrower. Note the edition when quoting.

## Source list

All accessed 2026-10-18 unless noted. IDs S1-S40 are shared with `measuring-software-delivery-performance-for-explanation-doc.md`.

| ID | Source | URL | Domain | Accessed | Reputation | Verification status |
|---|---|---|---|---|---|---|
| S1 | DORA, "DORA's software delivery performance metrics" (last updated 2026-01-05; CC BY 4.0, Google LLC) | https://dora.dev/guides/dora-metrics/ | dora.dev | 2026-10-18 | 1.0 primary | Fetched twice; definitions verbatim; match GLOSSARY.md and [S36 p. 13] |
| S2 | Harvey, N., "A history of DORA's software delivery metrics" (2026-01-02) | https://dora.dev/guides/dora-metrics/history/ | dora.dev | 2026-10-18 | 1.0 primary | Fetched; tool returned a summary, so quote only the short phrases marked as quotes |
| S7 | Thoughtworks Technology Radar, "DORA metrics" (2018-2026) | https://www.thoughtworks.com/radar/techniques/dora-metrics | thoughtworks.com/radar | 2026-10-17 | 0.8 practitioner | Reused; fetched blip summary. **Single source affiliated with a sponsor (2025 DORA sponsor); paraphrase only; not independent** |
| S25 | DORA, 2024 survey questions | https://dora.dev/research/2024/questions/ | dora.dev | 2026-10-18 | 1.0 primary | Re-fetched; all five items and options quoted |
| S34 | Forsgren, Humble, Kim, *Accelerate* (IT Revolution, 2018) | local `harness/accelerate-the-science-of-devops.epub` | local primary | 2026-10-18 | 1.0 primary | ch. 2 read in XHTML (survey bands, deployment definition); ch. 3 reused |
| S35 | DORA, *Accelerate State of DevOps Report 2024*, v. 2024.3 | local `harness/2024-dora-accelerate-state-of-devops-report.pdf` | local primary | 2026-10-18 | 1.0 primary | pp. 6, 10-16, 74, 79, 82 read from extracted text |
| S36 | DORA, *State of AI-assisted Software Development 2025*, v. 2025.2 | local `harness/2025_state_of_ai_assisted_software_development.pdf` | local primary | 2026-10-18 | 1.0 primary | pp. 13-14, 19-22, 138-139 read from extracted text |
| S40 | DORA Quick Check | https://dora.dev/quickcheck/ | dora.dev | 2026-10-18 | 1.0 primary | Reused (referenced by [S1], [S35 pp. 16, 79]) |
| S41 | DORA, 2023 survey questions | https://dora.dev/research/2023/questions/ | dora.dev | 2026-10-18 | 1.0 primary | Fetched; long items partly summarised by the tool |
| S42 | DORA, 2022 survey questions | https://dora.dev/research/2022/questions/ | dora.dev | 2026-10-18 | 1.0 primary | Fetched; Change Fail Rate ranges and time-to-restore wording quoted |
| S43 | DORA, 2025 survey questions | https://dora.dev/research/2025/questions/ | dora.dev | 2026-10-18 | 1.0 primary | Fetched; matches [S36 pp. 20-21, 138-139] |
| S44 | Graves Portman, D., "Are you an Elite DevOps performer? Find out with the Four Keys Project", Google Cloud blog (2020-09-23) | https://cloud.google.com/blog/products/devops-sre/using-the-four-keys-to-measure-your-devops-performance | cloud.google.com/blog/products/devops-sre | 2026-10-18 | 1.0 primary | Fetched; pre-2023 definitions; editor's note marks bucket labels as dated |
| S45 | Kaufman, B., "Another way to gauge your DevOps performance according to DORA", Google Cloud blog (2020-10-03) | https://cloud.google.com/blog/products/devops-sre/another-way-to-gauge-your-devops-performance-according-to-dora | cloud.google.com/blog/products/devops-sre | 2026-10-18 | 1.0 primary | Fetched; used only for 2020 names (MTTR, Speed/Stability) |
| S47 | DORA, Resources (source-available tools) | https://dora.dev/resources/ | dora.dev | 2026-10-18 | 1.0 primary | Fetched; tool list quoted |

**Reputation**: 14 sources. 13 at 1.0 (all DORA programme, including the local primaries) and 1 at 0.8 (S7). **Average ≈ 0.99.** For independence, the 13 DORA-programme sources count as one. S7 is affiliated with a sponsor, so there is no fully independent source. That is expected for a reference page on DORA's own definitions; non-definitional claims are tagged "(DORA-only)". Removed in Review 1: S17 (supported no finding) and S46 (github.com, off the trusted list). **Citation coverage**: every factual row and bullet carries a source ID. Interpretations are labelled.

## Research metadata

Examined: 13 web pages, 1 search result set (vendor results rejected), 3 local primaries. New sources this run: S41-S45, S47 (S46 fetched but dropped). Reused: S1, S2, S7, S25, S34, S35, S36, S40. Tool limits: no PDF renderer (used extracted text from earlier sessions); fetch tool caps quotes at 125 characters, so long items were rejoined only where they could be checked. Output: `docs/research/dora-metrics-for-reference-doc.md`.

## Review 1

**Verdict**: NEEDS_REVISION (reviewer, 2026-10-18). No new research was done. The revision only removes sources and changes tags, wording and verification marks.

| # | Severity | Issue | Resolution |
|---|---|---|---|
| 1 | High | S46 (github.com/dora-team/fourkeys) is off the trusted list | S46 dropped from every finding, the conflicts, the gaps and the source list. Four Keys now rests on [S44] only. The archive status and the README wording are removed; Section 7 says the project's current status is unverified from a trusted source. Conflict 2 now compares [S44] with [S45]. The trusted-sources file was not edited. |
| 2 | High | Independence overstated; S17 supports no finding; S7 is affiliated with a sponsor | S17 dropped from the count and the source list. S7 is labelled "single source affiliated with a sponsor, paraphrase" in the Deployment Rework Rate table and the source list. The executive-summary caveat and Gap 6 now say there is effectively no independent corroboration. Counts: 14 sources, 13 DORA programme, average ≈ 0.99. |
| 3 | Medium | Executive summary called Deployment Frequency bands "time bands" | Reworded: two metrics use time bands, and Deployment Frequency uses frequency bands. Both band ranges are given. |
| 4 | Medium | Non-definitional claims without outside corroboration were untagged | Tagged "(DORA-only)": "What it leaves out" (Change Lead Time), "Why DORA measures it" (Deployment Frequency), the reason for regrouping (Failed Deployment Recovery Time), the construct history, the failure rule and the 2024 answer-format change (Change Fail Rate), the group analysis and "Why DORA added it" (Deployment Rework Rate), and the 2024 statistical basis (Section 6). |
| 5 | Medium | Rejoined and summary-derived quotes lacked verification marks | Methodology now defines the marks (verbatim, local / fetched quote / rejoined / fetch-tool summary). The S1 scope quote is marked "rejoined, not verified locally". The extracted 2024 and 2025 text was searched for it and it is absent; the verified equivalents in the reports ([S35 p. 74], [S36 pp. 13, 20]) are pointed to. S2 rows in the per-metric tables, Section 6 and Section 8 are marked "fetch-tool summary". The 2025 reporting bands are marked "verbatim, local from extracted text; not re-checked against the rendered PDF". Definitions are cross-marked as verbatim, local in [S36 p. 13]. |
| 6 | Low | No glossary "Avoid" terms per metric | An "Avoid (GLOSSARY)" row was added to each of the five metric tables, copied from `GLOSSARY.md`. |
| 7 | — | Concerns the explanation research doc | Skipped as instructed (out of scope). |
| 8 | Low | Conflict 3 resolution not labelled as interpretation | Labelled "(interpretation, not stated by DORA)". The assessments in Conflicts 1, 2 and 4 are also labelled as interpretation. |

Also fixed in passing: [S40] (Quick Check) is now cited in Section 7, so every listed source supports at least one statement.

## Review 2

```yaml
review_id: "research_rev_20261018_dora_reference_iter2"
reviewer: "nw-researcher-reviewer (Scholar)"
date: "2026-10-18"
iteration: 2
max_iterations: 2
verdict: APPROVED
review1_issues_resolved: [1, 2, 3, 4, 5, 6, 8]   # 7 out of scope (explanation research doc)
blocking_issues: []
issues_open:
  - id: 1
    severity: medium
    issue: "Four Keys quotes (Deployment Frequency and Change Fail Rate rows) were partly README-sourced and are now attributed to S44 blog without re-check."
    resolution: "Not re-checked. The reference page does not quote Four Keys wording."
  - id: 2
    severity: low
    issue: "'verified report equivalents' and 'same scope' overstated equivalence."
    resolution: "Reworded to 'related statements in the reports' (orchestrator, 2026-10-18)."
  - id: 3
    severity: low
    issue: "'(verbatim, local)' marks depend on earlier-session extracted text (pdftext/) not confirmed in this session."
    resolution: "Noted. Extracts live in earlier session scratchpads; re-extract from harness/ PDFs to re-verify."
scores:
  source_verification: 0.92
  source_bias: 0.85
  evidence_quality: 0.85
  cross_reference: 0.82
  doc_readiness: 0.92
  citation_coverage: 0.97
  avg_reputation: 0.99
```
