---
name: keyword-led-compounding-engineering
description: Improve an existing SEO data product one important keyword at a time by benchmarking the searcher's task, improving shared data and application systems, verifying benefits across page families, and making the result refresh automatically. Use for autonomous SEO engineering, programmatic SEO quality, keyword campaigns, and continuous product improvement.
license: MIT
---

# Keyword-Led Compounding Engineering

A companion to [Computed Knowledge SEO](../computed-knowledge-seo/SKILL.md).

## Principle

**One keyword at a time. Improve the system, not just the page.**

Select one commercially or strategically important search intent. Use its canonical page as a demanding acceptance test for the whole product. Stay on that target across successive engineering cycles until the buyer or user's task is served exceptionally well, with independently useful computed knowledge and verified ongoing maintenance. Then move to the next target. Improvements to shared capabilities must benefit previous and future pages too.

The aim is to make the best answer in the relevant search market, not to guarantee a ranking or claim objectively universal superiority.

## 1. Select and persist one target

Start with the site's current strategy, architecture, production state, existing tracker, source permissions and safety rules. Select a query cluster using:

- Country-specific keyword demand, relevance to the intended audience, and commercial or strategic value.
- Real search intent and competing organic results, not volume alone.
- Current data coverage, defensible source access, attainable differentiation and cost.
- Shared leverage: how much of the product improves if this buyer task is solved?

Map close variants to one canonical intent; do not double-count pooled keyword volumes or create duplicate routes. Keyword Planner competition is advertiser competition, not organic ranking difficulty. Use verified domain metrics when available.

Keep one active campaign per site in durable project state. Record the keyword, market, canonical candidate, rationale, status, baseline, benchmark, current bottleneck, dependencies and next action. Do not pick a different keyword each day.

## 2. Define the best answer before building

Inspect the actual search results in the target market. Sample the top 5–10 relevant organic competitors where available. Record date, market, URLs, intent, task flow, useful data and evidence, freshness, coverage, filters, comparisons, mobile UX and next action. Exclude irrelevant or navigational results rather than treating them as the same task. Missing access is UNKNOWN.

Translate the query into a concrete user task and realistic scenarios. Compare the existing live page and underlying product against the same task. Ask:

- Can the user actually find what the query promises?
- Can they narrow and compare results, understand uncertainty and make a decision?
- Which important questions are competitors answering well?
- What useful answer could we compute that competitors do not provide?
- What is missing from our source coverage, entity resolution, data quality or functionality?

For listing or catalogue tasks, use a fixed, dated, independently sourced sample of relevant eligible records (suggested 25–50 initially, subject to rights and feasibility). Measure recall, accuracy, duplicates, freshness and unknowns. Distinguish missing ingestion, failed extraction, legitimate exclusion and inaccessible sources. Do not estimate full-market coverage from a convenience sample.

## 3. Trace the gap to a shared capability

Prefer changes in this order when supported by evidence, with critical correctness, security and privacy issues always taking precedence:

| Layer | Examples |
| --- | --- |
| Source acquisition | Lawful feeds, independent sources, coverage gaps, reusable adapters |
| Normalization and identity | Deduplication, taxonomy, units, source scope, entity resolution |
| Knowledge and computation | Cross-source joins, deterministic metrics, temporal observations, claim ledger |
| Product functionality | Relevant search, filters, maps, comparison, alerts, agent/API parity |
| Presentation | Shared template, provenance, methodology, useful internal links and next steps |
| Technical delivery | Canonical/indexability, accessibility, latency, crawlable rendering |

Do not hardcode a metric, record, paragraph or special-case implementation to make the target URL look better. Write the system that generates the answer. Follow the companion skill's graph, claims, source rights, uncertainty and validation rules.

## 4. Run one bounded engineering cycle

For each invocation:

1. Reopen current campaign state, live evidence, latest code, existing work, CI and deployment status. Do not duplicate another agent's work.
2. Identify the highest-value remaining buyer-task gap and trace its root cause. State the before condition, hypothesis, shared capability and acceptance check.
3. Implement one safe, reversible product/data/UX improvement if authorized and feasible. Reuse existing services and templates. Do not substitute a report or cosmetic edit for a production change.
4. Test the target and at least two relevant, differently populated beneficiary cohorts, plus appropriate missing, stale, withdrawn, empty or conflicting-data controls. Check equivalent web/API/agent behavior where applicable.
5. Follow the repository's validation, commit, review, merge and deployment rules. Record implemented, tested, merged, deployed, live-verified and measured outcomes separately. Never mark unavailable checks as passed.
6. Record the before/after result, affected page families, actual beneficiaries where measurable, evidence, blocker and next action in the existing tracker.

If blocked, solve an independent gap within the same campaign or a critical shared blocker. If no safe meaningful change is possible, report the precise blocker rather than inventing busywork. Do not bypass permissions or spend without authorization.

## 5. Make every improvement compound automatically

Integrate the capability with the site's existing ingestion, normalization, computation, snapshot and publication pipeline. Prefer idempotent refresh jobs, independent of page rendering, with source version, timestamps, freshness thresholds, retries, monitoring and fail-closed behavior. Preserve permitted historical observations; do not overwrite history or equate missing data with zero.

Daily refresh is a product requirement when source cadence supports it, not a claim that an agent runs daily. Respect slower source release cycles, cost and licensing. Verify the actual production job and its outputs; a cron file, merged commit or configured automation alone is not proof.

Changes in underlying facts should update all relevant eligible pages and tools without individual content rewrites or unnecessary redeploys. Protect prior campaigns with regression checks and reopen them when coverage, accuracy, freshness or buyer utility degrades. New pages still require distinct intent and publication gates.

## 6. Graduate using a measurable quality gate

Suggested rubric: score each dimension 0 (absent/failing), 1 (partial), or 2 (verified strong). Record evidence, denominator and sample size; UNKNOWN cannot score 2.

| Dimension | Maximum |
| --- | ---: |
| Relevant data/inventory and coverage | 2 |
| Accuracy, provenance and freshness | 2 |
| Discovery/search/filter experience | 2 |
| Original, independent computed knowledge | 2 |
| Comparison/decision support and meaningful next action | 2 |
| Mobile UX, accessibility and performance | 2 |
| Technical SEO, canonical and discovery | 2 |
| Automated refresh and quality monitoring | 2 |

Suggested graduation gate: >=14/16, no zero, no critical task disadvantage against the sampled best competitor, no severe unsupported claims, at least one independently useful differentiated computed answer, verified refresh and all applicable release gates passed. For inventory tasks, consider >=80% recall on the fixed eligible audit sample and zero severe false inclusions as initial proposed targets; calibrate to domain and baseline before implementation. Never redefine the sample to manufacture a pass.

This rubric is a proposed operational tool, not a Google ranking factor or a universal guarantee. Adapt it explicitly to the site's domain and risk; do not silently waive essential gates.

Once the product gate passes, enter MONITORING and select the next keyword based on evidence. Do not wait indefinitely for #1 rankings. Observe search visibility and qualified actions over 14–28 days or an adequate sample, and reopen the campaign if it regresses. Product quality, ranking, traffic and revenue are separate outcomes.

## 7. Worked example: rural property

Target query: **smallholdings for sale Wales**. Candidate page: a canonical country × property-type collection, confirmed against the site's existing architecture. The actual market benchmark and results must be measured, not assumed.

Searcher task: find real current Welsh smallholdings within budget; distinguish existing dwellings from undeveloped plots; understand the acreage actually included; compare price, setting, access and constraints; save or contact the original agent.

| Target gap | Shared system change | Other beneficiaries |
| --- | --- | --- |
| Missing valid properties | Improve permitted agency acquisition and coverage checks | Other counties and categories |
| Incorrect land or dwelling details | Improve extraction, typed offer scope and eligibility | All search and property pages |
| Weak price comparisons | Compute current cohort distributions with denominators and dates | Every region/type market page |
| Missing location context | Join appropriate independent geographic sources with explicit coverage | Property detail and other location pages |
| Poor search experience | Improve shared search, filter and compare components | Every eligible category |
| Stale listings | Automated observation, status and withdrawal handling | All listings and alerts |

For Welsh data, check jurisdiction and rights; an England-only source is not Welsh coverage. Do not confuse asking price with sold price, land nearby with land included, or mapped paths with verified access rights.

This is an illustrative process, not evidence that any particular site has completed these improvements.

## Campaign record template

~~~yaml
id: KW-01
query: ""
market: ""
canonical: ""
status: BASELINE_REQUIRED # ACTIVE | BLOCKED | MONITORING | GRADUATED
demand:
  source: ""
  observed_at: ""
  monthly_estimate: null
  limitations: ""
buyer_task: ""
competitor_evidence: []
baseline: {}
fixed_audit_cohort: {}
quality_scores: {}
current_bottleneck: ""
shared_capability: ""
beneficiary_cohorts: []
refresh_evidence: ""
last_change:
  commit: ""
  checks: []
  deployment: UNKNOWN
  live_evidence: ""
next_action: ""
reopen_conditions: []
~~~

Use the existing project tracker rather than create a second competing work board.

## Daily report

Active keyword and canonical; buyer gap and baseline; shared capability changed; target and cross-cohort verification; automatic refresh evidence; tests, commit and live status; remaining blocker and next action. Report actual qualified outcomes when measured, not projected gains as facts.

**Scale capabilities, not bespoke pages. Keep the current keyword until the buyer task is excellent, then let the next campaign improve the previous ones too.**
