# Presentation Script (EN) — "Đoàn Trung Nguyên · Analytics Engineer"

**Deck:** `presentations/analytics-engineer-intro.html` · 11 slides
**Audience:** partner / client stakeholders (mixed business + technical)
**Default runtime:** 16–18 minutes talk + 10 minutes Q&A
**Also included:** a 7-minute short version, a 90-second version, and Q&A prep

---

## 0. Before you present

**Deck controls you'll actually use:**

| Key | Action | When |
|---|---|---|
| `F` | Fullscreen | Always, before you start |
| `→` / `Space` | Next slide | Throughout |
| `←` | Previous | Going back in Q&A |
| `1`–`9` | Jump to slide | Q&A — see caveat below |
| `L` | Toggle EN / VI | If the room switches to Vietnamese |
| `P` | Print / export PDF | To send the deck afterwards |
| `N` | Speaker notes | **Not while sharing your screen** |
| `?` | Shortcut help | Only if you forget |

**Three things to check before the call:**

1. **Press `F` for fullscreen first.** The deck is `100vh`-based, so without fullscreen the browser chrome eats the bottom of slides 5 and 7, which are the two longest.
2. **Don't press `N` while screen sharing.** The speaker notes panel renders in the same window, so the audience sees it. Keep this script on your phone or a second monitor instead.
3. **Number keys only reach slides 1–9.** Slides 10 (Education) and 11 (Closing) need `End` or arrow keys. If a partner asks about your background mid-talk, use `End` then `←` rather than fumbling.

**Two mechanical notes:**

- Slides **5** and **7** are scrollable. On a small share window you may need to scroll to reach the last card. Know that in advance so you're not surprised live.
- The left and right **9% of the screen are click zones** for next/previous. If you're presenting from a tablet, tap-forward works; also swipe.

**Language:** the deck ships bilingual. If your partner is more comfortable in Vietnamese, press `L` and deliver the Vietnamese version — the content is identical. This script assumes English delivery.

---

## 1. Title — 45 seconds

*(Screen: name in gradient, role line, contact chips, "Attitude is everything.")*

> "Good morning, and thank you for the time. My name is Đoàn Trung Nguyên, and I'm an Analytics Engineer working across data modeling and data governance.
>
> The one-line version of what I do: **I build the trusted data layer that analysts and business teams run on.** Not the pipelines that move data, and not the dashboards at the end — the layer in the middle that decides whether the number on the dashboard is actually right.
>
> I've got about fifteen minutes of material and I'd rather leave room for your questions, so let me move."

**Delivery note:** resist the urge to linger on the title slide. Say the one-liner and advance. Your contact details reappear on the closing slide, so nobody needs to write them down now.

---

## 2. About me — 2 minutes

*(Screen: three cards — Analytics Engineering, Data Modeling · Data Vault 2.0, Data Governance & Quality — plus four stat tiles)*

> "My work sits on three pillars, and I'd like to be precise about how they relate, because the third one is the reason the first two matter.
>
> **First, analytics engineering.** Advanced SQL and dbt on cloud warehouses. Concretely, that means I build layered models — staging, intermediate, marts — that are tested, documented, and reusable. The layering isn't aesthetics. It's what lets you change a source system without rewriting forty reports.
>
> **Second, data modeling, and specifically Data Vault 2.0.** I design and implement Data Vault for enterprise warehouses, with star-schema information marts on top for BI to consume. I'll come back to why that combination in a few slides.
>
> **Third, data governance and data quality.** Quality rules with agreed thresholds and alerting, metadata and lineage, documentation standards, and the written procedures that keep it all in place.
>
> Here's the connection between them. The first two pillars make models **correct**. The third is what makes them **trustworthy**. Those aren't the same thing. A correct model that nobody can find, nobody understands, and nobody gets alerted about when it breaks — that model doesn't get used. Or worse, it gets used after it's silently wrong."

*(Point at the stat tiles.)*

> "For context: about four years working in data, two of them specifically as an Analytics Engineer, dbt Certified Developer, and I work in English day to day — IELTS 7.0, and my degree was taught in English."

**Delivery note:** the "correct versus trustworthy" distinction is the intellectual spine of this whole deck. Land it slowly here and you can reference it three more times later.

---

## 3. Where I sit — 2 minutes

*(Screen: the flow diagram — Sources → Data Engineer → **Analytics Engineer** → Analyst/BI → Business — with two cards below)*

> "Because 'Analytics Engineer' is still a newish title, let me show you exactly which seam I own.
>
> Data comes from source systems — transactional databases, APIs, files. A **data engineer** ingests it and lands it in the warehouse. Their job is that the data arrives, reliably and on time.
>
> Then me. **I make it mean something.** Raw landed tables become business concepts: what a customer is, what a transaction is, how you count an active account.
>
> Then **analysts and BI** explore and report on top of that, and the **business** makes decisions.
>
> The value of naming this seam is that it used to be nobody's job. Data engineers were asked to understand business logic they'd never been briefed on. Analysts were asked to write production-grade SQL between two meetings. So the same business logic got reimplemented in fifteen dashboards, in fifteen slightly different ways, and then people argued in meetings about whose revenue number was correct."

*(Point at the left card.)*

> "So what I own is four things: **the data models**, the **business logic and metrics defined once and reused everywhere**, the **tests that fail loudly before a report does**, and the **documentation and lineage** that let people self-serve instead of queueing for my time.
>
> That's the contract, and I'd state it plainly: **what I deliver to the business is a tested, documented, clearly named dataset.** Not a query I ran for you once."

*(Point at the right card.)*

> "And how I work — four habits.
>
> I apply **software practices to data**: Git, code review, CI, modular design. Data transformation is code, so it should be reviewed and tested like code.
>
> I **start from the business question, not the table.** If I don't know what decision a model serves, I'm guessing at the grain and the metrics.
>
> I **agree thresholds with data owners, then automate the check.** More on that shortly, but the sequence matters — agreement first, automation second.
>
> And: **if it isn't documented, it isn't done.** I treat that as part of the definition of done, not a nice-to-have for later."

---

## 4. Experience — 1.5 minutes

*(Screen: three-item timeline, current role highlighted in amber)*

> "Quick walk through how I got here, because the direction is the point.
>
> I **started close to the business.** At OpenCommerce Group I was a data analyst moving into analytics engineering — building Airflow DAGs, designing star schemas, and writing the data dictionary and business glossary. That last part is where I learned that ambiguous definitions cause more damage than broken pipelines.
>
> Then I went **deeper into BI and quality** at Mcredit — dashboards built around a high data-ink ratio, meaning every pixel carries information; data quality monitoring; profiling in Python; and metadata management.
>
> And **now I own modeling and governance in a regulated financial domain** — LPBank Securities, on dbt and Amazon Redshift, building the ELT layer, the data quality framework, and the governance policies.
>
> The arc is: from consuming data, to modeling it, to governing it. Each step I got closer to the source of trust rather than further from it."

**Delivery note:** don't read the tag pills. They're there for the partner to scan, and for whoever reads the PDF afterwards.

---

## 5. Current role · LPBank Securities — 3 minutes

*(Screen: five cards. This slide scrolls — check you can reach the bottom card.)*

> "I want to spend the most time here, because this is the most demanding environment I've worked in and it shaped how I think.
>
> Start with the context that changes everything: **in securities, a wrong number isn't an inconvenience — it's a compliance problem.** In e-commerce, if a dashboard is off by two percent, someone makes a slightly worse decision this week. In a regulated financial domain, a wrong figure can go into a report that goes to a regulator. That difference is why everything on this slide exists."

*(Card 1.)*

> "**Modeling on dbt and Redshift.** I design, build and maintain analytics-ready models that turn raw source data into trusted datasets — for business reporting and for the analytics that sit downstream of it."

*(Card 2.)*

> "**Reusable, scalable ELT.** Pipelines built to analytics engineering best practice, which shows up as three things: consistency, so the same concept is computed the same way everywhere; maintainability, so the next person can change it safely; and model performance, which on Redshift is a real cost line, not just a nice-to-have."

*(Card 3.)*

> "**Automated data quality validation.** Threshold-based monitoring and alerting that catches anomalies proactively — before they reach a report, and certainly before they reach a regulator. The word doing the work there is *proactively*. The alternative is finding out from a business user, which means the damage already happened."

*(Card 4 — slow down here.)*

> "**Governance built into the workflow.** This is the design decision I'd most want you to take away.
>
> Most governance programmes fail the same way: they exist as a separate process. A document nobody reads, a spreadsheet nobody updates, a review meeting people learn to route around. It's parallel to the work, so it decays.
>
> My approach is to make **dbt itself the governance surface.** Standardised modeling patterns, automated testing, documentation, and lineage all live in the same repository as the transformation code, and they run on every build. Governance stops being a thing you remember to do and becomes a thing you can't skip — because the build fails.
>
> That's the difference between a governance policy and governance that actually holds."

*(Card 5, full width.)*

> "And then the written layer: **policies, standards and operating procedures.** Data quality rules, documentation standards, governance processes.
>
> This is the part that looks like bureaucracy and isn't. Automation holds while I'm the one maintaining it. Written standards are what keep trusted data assets trustworthy **as the team grows** — when there are five people writing models instead of one, and I'm not reviewing every pull request personally."

---

## 6. Data Vault 2.0 — 2.5 minutes

*(Screen: Hub / Link / Satellite boxes, the DV → OBT → SMY flow, and the four-point "why" list)*

> "This is my deep specialisation, so let me make it concrete rather than academic.
>
> Data Vault 2.0 splits the warehouse into three kinds of object.
>
> **Hubs** hold business keys — the things the business actually talks about. A customer. An account. An instrument.
>
> **Links** hold the relationships between those things, over time. This customer held this account, during this period.
>
> **Satellites** hold the descriptive attributes and the **full history of change**. Not just what the customer's status is now — what it was, and when it changed.
>
> Now, why accept that extra complexity? Four reasons, and the first one is why it fits financial data specifically."

*(Point at the "why" list.)*

> "**It's auditable by design.** Every record keeps its source and its load timestamp. So the question 'where did this number come from, and when did we learn it' has a structural answer, not an archaeological one. In a regulated domain that question gets asked, and you want the answer to take minutes.
>
> **It absorbs change.** When a new source system arrives — and one always does, after an acquisition, a migration, a new product — you attach it without reshaping existing history. Compare that to a classic dimensional warehouse, where a new source often means restating dimensions and rebuilding history. That's the failure mode Data Vault is designed to avoid.
>
> **It loads in parallel.** Hubs, links and satellites are independent of each other, so loads don't serialise behind one another. That matters when the load window is fixed.
>
> And critically — **it stays BI-friendly on top.**"

*(Point at the DV → OBT → SMY flow.)*

> "Because I should be honest about the trade-off: nobody wants to write analytics queries directly against a Data Vault. Joining hubs, links and satellites for a simple question is genuinely unpleasant.
>
> So the raw vault isn't what analysts touch. Above it I build a **One Big Table** layer — wide, denormalised, join-free — and above that **summary tables** for the specific questions people ask repeatedly.
>
> The result is the split you want: **auditability and change-absorption underneath, simplicity and speed on top.** Analysts get a flat table. Auditors get full lineage back to the source. Neither one pays for the other's requirement."

**Delivery note:** if the room is purely business, compress this to the three shapes plus the auditability point, and skip the parallel-loading detail. If there's a data architect present, this is the slide where they'll test you — invite it.

---

## 7. Data quality — 3 minutes

*(Screen: the five-step flow, then four cards. This slide scrolls.)*

> "This is my day-to-day loop, and there's one structural claim I'd make about it: **the whole loop lives inside dbt.** No side scripts, no separate quality tool, no second place where truth is defined. Five steps.
>
> **One — profile in SQL.** Before I write a single rule, I look at what the data actually does. Null rates, distributions, cardinality, outliers. You cannot set a sensible threshold on data you haven't looked at.
>
> **Two — agree the threshold.** And this is the step most teams skip, so let me be emphatic: **a threshold is a business agreement, not a technical guess.** If I decide alone that this field must be 99% complete, I've invented a rule. When the data owner and I agree it together, two things happen — the number is right, and when the alert fires, someone owns it. A rule with no owner is noise that people learn to ignore.
>
> **Three — codify it as a dbt test.** The agreement becomes code, in the repository, next to the model it protects.
>
> **Four — alert on failure.** Automatically, to the people who agreed the threshold.
>
> **Five — store and track the results.** Which turns quality from an event into a trend."

*(Card: Dimensions.)*

> "The dimensions I monitor by default are **completeness, uniqueness and validity** — the three that catch most real problems. Then I extend into **accuracy, consistency and timeliness** where the data owner needs it. I add dimensions on demand rather than monitoring everything, because a quality suite nobody trusts is worse than a small one everybody does."

*(Card: One toolchain.)*

> "On the tooling — everything is dbt tests. **Generic tests** for the common rules, **singular tests** for the one-off business logic, and **custom generic tests** where I need to reuse a rule across many models. Thresholds get encoded with **severity** and **`warn_if` / `error_if`**, which is how the agreed number ends up literally in the code — warn at this level, fail the build at that level.
>
> Why one toolchain matters: every separate quality tool becomes a second definition of the truth that drifts from the first. Keeping it in dbt means one place, one review process, one history."

*(Card: Tested and versioned like code.)*

> "The tests live in **Git, next to the models they protect**, and run on **every build**. So a quality rule can be reviewed in a pull request, changed with a visible history, and audited later. If someone asks 'when did we relax this rule, and who approved it' — that's a Git log, not a conversation."

*(Card: Quality as a visible metric — full width.)*

> "And the last piece, which changes how the business relates to quality.
>
> Test results are written **back into the warehouse** — dbt's `store_failures` — and surfaced on dashboards. Two consequences.
>
> First, **data health becomes a trend**, so you can say 'completeness on this domain has degraded three weeks running' instead of 'the build is red today'.
>
> Second, and more practically: the owner gets **a concrete list of the failing rows.** Not a red build they can't act on — the actual records to fix. That's the difference between a quality report that generates work and one that generates arguments."

---

## 8. Governance & metadata — 2 minutes

*(Screen: "Documentation is infrastructure", four cards)*

> "The header is the argument: **documentation is infrastructure.**
>
> Documentation gets treated as overhead — the thing you'll do after the deadline, which means never. I'd argue it's load-bearing, and here's the case in four parts.
>
> **Technical and business metadata.** A data dictionary and a business glossary, kept current, so that a metric **means the same thing in every room of the company.** If sales, finance and risk each have their own definition of an active customer, you don't have a data problem, you have three organisations quietly disagreeing — and the meeting where that surfaces is always expensive.
>
> **Onboarding at speed.** New team members find answers themselves instead of queueing for tribal knowledge. Concretely: a new analyst's ramp-up stops being a tax on your senior people's calendars.
>
> **Lineage for impact analysis.** Before I change a model, I know what breaks downstream — **and who to tell.** Both halves matter. Knowing what breaks prevents the outage; knowing who to tell is what makes people trust you enough to let you change things quickly.
>
> And the fourth one is newer, and it's why I put 'AI-ready' on the title slide. **Metadata is fuel for AI.** Everyone wants to point a language model at their company data. The reason those projects disappoint is almost never the model — it's that the data has no semantic layer. The model doesn't know which of six revenue columns is the one people mean, or that this table was deprecated last quarter. Curated metadata is exactly that missing context.
>
> So the line I'd leave you with: **metadata is how a team stops re-answering the same question.** And it's now also what makes AI on top of your data accurate rather than confidently wrong."

---

## 9. Toolbox — 1 minute

*(Screen: five card groups of tag pills)*

> "I won't read this list — it's here for reference and it'll be in the PDF. Let me just characterise it honestly.
>
> **SQL and dbt are where I'm strongest** — that's the core of the craft, and where I'd expect to add value from day one.
>
> **Python is my utility knife.** Profiling, automation, the things SQL is awkward for. I'm not claiming to be a software engineer.
>
> **Warehouses:** Redshift in depth right now, BigQuery before that, and Airflow for orchestration.
>
> And **I know the BI layer well enough to model for the person consuming it** — Power BI, Holistics, dbt docs. That's not a long list of BI tools, deliberately. The point isn't tool coverage; it's that I've sat on the consuming side, so I model with the end user's constraints in mind rather than handing over a technically correct schema that's miserable to query."

**Delivery note:** one minute maximum. Tool lists are the least differentiating slide in any deck — the honest framing of *strongest / utility / adjacent* is worth more than the pills themselves.

---

## 10. Education & certificates — 1 minute

*(Screen: NEU degree, certificates, the full-width closing card)*

> "Briefly on background, and I want to frame this deliberately.
>
> My degree is a **Bachelor of Business Administration, taught in English, from National Economics University, graduated with Distinction.** Business, not computer science.
>
> I present that as a **feature, not a detour.** It's the reason I can sit in a business conversation and leave with a modeling specification — because I understand the problem being described, not just the tables being requested. The translation step between business and data is where most requirements get lost, and I don't need a translator for it.
>
> On top of that: **dbt Certified Developer**, Google Data Analytics, IELTS 7.0. And currently going deep on **data governance** — DAMA-DMBOK, the DCAM framework, data quality scoring methods, and local data regulations, which matter a great deal in a regulated domain.
>
> The summary is on the card: **the business degree is why I start from the decision and work backwards to the model. The technical craft is why the model holds up in production.** You need both. One without the other gives you either a beautiful warehouse nobody uses, or a useful report that falls over every month."

---

## 11. Closing — 1 minute

*(Screen: three cards, the "Data-Head" line, contact chips)*

> "To close, three things I'd bring to a partnership.
>
> **Business first.** I translate between business and technical teams, and I model for the decision that has to be made — not for the data that happens to be available.
>
> **Engineering discipline.** Version control, modular models, automated tests, CI. Data work treated like software, because the alternative is a warehouse nobody dares to change.
>
> **Governance mindset.** Quality rules, metadata and lineage in place from day one — so **trust scales with the platform** instead of degrading as it grows. That's the failure I've seen most often: the data platform grows and confidence in it shrinks. It's avoidable, and it's avoidable early and cheaply, or late and expensively.
>
> And I'll say plainly: I'm prepared to be **hands-on at every step**. I'm not looking to hand over a diagram and step back. I'm still building — on my way to being a genuinely skilled 'Data-Head'.
>
> My details are on screen. Thank you — I'd be glad to take questions."

**Then stop talking.** Leave the slide up; the contact chips are on it. Let the silence sit for a few seconds rather than filling it.

---

## 12. Q&A preparation

**"What does an Analytics Engineer do that our data engineer doesn't?"**
> Your data engineer makes sure the data arrives — reliably, on time, at scale. I make sure it **means the right thing** once it's there. Different skill and different failure mode: their bad day is a pipeline that didn't run; mine is a pipeline that ran perfectly and produced a number that's subtly wrong. Practically, I take business logic out of dashboards and put it in one tested, documented place.

**"Why dbt specifically? Couldn't you do this with stored procedures?"**
> Functionally you can transform data either way. What you don't get from stored procedures is the surrounding system: dependency-aware execution, testing as a first-class feature, documentation and lineage generated from the same code, and a Git-based review workflow. My governance model depends on all of that being in one place. With stored procedures, governance becomes a separate process again — and separate processes decay.

**"Isn't Data Vault overkill for our size?"**
> Very possibly, and I wouldn't propose it by default. Data Vault earns its complexity when you have **many source systems, real auditability requirements, and sources that keep changing**. If you have three stable sources and no regulator, a well-built dimensional model is the right answer and I'd say so. What I'd want to know before recommending either: how many sources, how often they change, and whether anyone external audits your numbers.

**"How long before we'd see something working?"**
> Depends on the state of the landed data, and I'd want to look before committing to a number. The sequencing I'd propose: profile the sources and agree the priority business questions first, then a thin vertical slice — one domain, modeled end to end with tests and documentation — rather than a broad foundation with nothing consumable on top. A working slice is what gets you feedback while the design is still cheap to change.

**"Who owns data quality in your model — you or the business?"**
> Shared, and the split is deliberate. The **business owns the threshold** — what level of completeness or accuracy is acceptable is a business decision, not a technical one. I own **implementing, automating and reporting** it. That split is why the alerts get acted on. If I set the thresholds alone, failures become my problem to explain rather than the owner's problem to fix.

**"You mention four years in data, but the timeline starts in April 2023. Can you walk me through that?"**
> **Prepare a real answer for this one.** The visible timeline covers roughly three and a bit years, so if the four-year figure includes earlier work — internships, a prior role, part-time analytics — say so specifically and briefly. If it doesn't, change the stat tile in the deck to match the timeline. A sharp partner will do this arithmetic, and it's a cheap thing to get exactly right.

**"What would you want from us to get started?"**
> Four answers, and they change most of my recommendations: your **warehouse**, your **source systems and how stable they are**, whether you have **external audit or regulatory reporting obligations**, and who the **data owners** are — the people who can actually approve a threshold. That last one is usually the hardest to get and the most important.

**"Do you work in English day to day?"**
> Yes. My degree was taught in English, IELTS 7.0, and I currently work in English. This deck also has a Vietnamese mode if that's easier for anyone on your side — *(press `L` to show it, then press `L` again)*.

**"Can you send us this?"**
> Yes — press `P` and export to PDF. Worth offering proactively at the end.

---

## 13. Short version — 7 minutes

Five slides. Skip 4 (timeline), 9 (toolbox), 10 (education) unless asked.

| Slide | Time | The one thing to land |
|---|---|---|
| **1. Title** | 20s | "I build the trusted data layer that analysts and business teams run on." |
| **2. About** | 60s | Three pillars, and that governance is what makes models *trustworthy*, not just *correct*. |
| **3. Where I sit** | 90s | The seam between data engineering and the business. My deliverable is a tested, documented, named dataset. |
| **5. Current role** | 2m | Regulated domain: a wrong number is a compliance problem. Hence governance built **into** the workflow — dbt as the governance surface, not a parallel process. |
| **7. Data quality** | 2m | The five-step loop, all inside dbt. Thresholds are a business agreement. `store_failures` turns quality into a tracked metric with an actionable row list. |
| **11. Closing** | 45s | Business first, engineering discipline, governance mindset. Hands-on. |

If you have a spare minute, add **slide 8** (metadata as AI fuel) over slide 5 — it's the most forward-looking point in the deck and it lands well with executives.

---

## 14. Ninety-second version

> "I'm Đoàn Trung Nguyên, an Analytics Engineer. I own the layer between your data engineers and your analysts — the part that turns landed raw tables into business concepts that can be trusted.
>
> Three pillars: modeling with dbt on cloud warehouses, Data Vault 2.0 for enterprise warehouses with star-schema marts on top, and data governance and quality. The third is what makes the first two trustworthy rather than merely correct.
>
> Right now I do that at LPBank Securities, on dbt and Redshift, where a wrong number is a compliance problem rather than an inconvenience. So the quality loop is automated and lives entirely inside dbt: profile the data, agree the threshold **with the data owner**, codify it as a test next to the model, alert on failure, and store the results so data health is a trend with an actionable row list — not just a red build.
>
> The principle behind all of it: governance built **into** the workflow, never beside it. Governance that runs parallel to the work decays. Governance that fails your build doesn't.
>
> My background is business — a BBA with Distinction — which is why I start from the decision and work backwards to the model. The technical craft is why the model holds up in production."

---

## Delivery notes

- **Total silence beats filler.** After the closing line, stop. Don't add "so, yeah, that's me."
- **Never read a card.** Every slide is written to be scanned by the audience while you say something adjacent to it. Read the cards aloud and you're redundant; characterise them and you're additive.
- **Slides 5 and 7 are the substance.** If you're running short on time, cut from slides 4, 9 and 10 — never from 5 or 7.
- **The strongest three lines in the deck**, worth memorising verbatim: "correct is not the same as trustworthy", "a threshold is a business agreement, not a technical guess", and "governance that runs parallel to the work decays."
- **Own the Data Vault trade-off out loud.** Saying "nobody wants to query a Data Vault directly, which is why I build OBT and summary layers on top" reads as judgement, not weakness. Pretending there's no trade-off reads as inexperience to anyone who's built one.
- **Have the four-years question answered before you present it.** See Q&A. It's the only internal inconsistency a sharp partner can find in the deck, so make it a non-event.
