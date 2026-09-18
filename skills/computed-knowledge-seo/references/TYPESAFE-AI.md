# TypeSafe AI integration

## Role

Use TypeSafe AI as a **semantic compute layer** when the pipeline needs fast, typed judgments over language.

Do not use it to replace ordinary code.

The governing rule:

> **Use TypeSafe to compute meaning. Use code to compute numbers. Persist both.**

TypeSafe’s System One pattern is useful because semantic judgments return bounded typed answers and probabilities rather than free-form prose.

Before implementing against TypeSafe, read the current upstream skill and live docs. API contracts and model details can change.

Upstream skill:
https://github.com/typesafe-ai/skills/blob/main/skills/typesafe-ai/SKILL.md

Docs index:
https://docs.typesafe.ai/llms.txt

## Good uses

Use TypeSafe for:

- job-function classification
- AI-specialism classification
- deciding whether a source supports a candidate semantic relation
- mapping messy labels into a canonical taxonomy
- bounded relevance judgments
- evidence reranking
- claim-support checks
- routing ambiguous records
- semantic feature discovery

Do not use TypeSafe for:

- exact arithmetic
- database joins
- unit conversion
- time-series aggregation
- deterministic rankings
- copying known structured values
- generating filler prose

## Primitive mapping

### Choice

Use when exactly one of a defined set should be selected.

Examples:

- engineering / research / sales / operations / other
- foundation models / agents / healthcare AI / robotics / other
- company / product / model / dataset / person

### Noul

Use for a yes/no semantic relation.

Examples:

- Does this source support that the company builds AI agents?
- Is this role customer-facing?
- Does this paragraph support the rendered claim?
- Is this page primarily about a specific company?

### Score

Use for an ordered semantic dimension.

Example:

How directly is a role focused on AI-agent engineering?

- none
- peripheral
- substantial
- core

Keep levels concrete and independently understandable.

## Persist semantic judgments

Do not rerun the same classification every time a page renders.

Store:

~~~yaml
semantic_feature_id: sf_123
subject_id: job_987
feature: belongs_to_function
value: engineering
probability: 0.96
source_record_id: src_456
source_hash: sha256:...
question_schema_version: job_function_v3
model: jev
observed_at: 2026-09-18
created_at: 2026-09-18T09:00:00Z
~~~

If source text or question schema changes, recompute the affected features.

## Batch independent questions over the same state

If one job description needs several independent judgments, ask them together when supported:

- function
- agent-related?
- model-training-related?
- customer-facing?
- seniority band

Then persist all results.

Do not combine dependent questions that require an earlier answer to fetch new evidence.

## Cascade design

Prefer:

~~~text
deterministic rules
→ unresolved cases only
→ TypeSafe
→ uncertain / high-impact cases only
→ reasoning LLM or human review
~~~

Examples:

- explicit department field says “Engineering” → deterministic;
- title “Forward Deployed AI Architect, Strategic Accounts” → semantic judgment;
- low-confidence or business-critical classification → deeper review.

This keeps inference cost concentrated on ambiguity.

## Reuse features across outputs

A single persisted feature can support:

- entity pages
- category pages
- trend analysis
- rankings
- comparison pages
- research reports
- APIs

Example:

~~~text
job descriptions
→ TypeSafe job-function classification
→ stored features
→ SQL hiring-mix aggregation
→ 90-day time series
→ “AI companies increasing research hiring”
~~~

The semantic model should not calculate the 90-day growth. Code should.

## Claim verification

A useful final semantic check is to compare a rendered sentence with its evidence bundle.

Example evidence:

> 61% of observed openings are commercial roles.

Potential rendered sentence:

> The company has aggressively pivoted toward commercialization.

A verifier should reject or flag this because “pivoted” implies temporal change and “aggressively” adds an unsupported interpretation.

The fix is not better prose. The fix is to constrain rendering to validated claims unless a separate temporal computation supports the stronger statement.

## Feature maturation

Over time:

~~~text
TypeSafe judgments
→ stored labeled features
→ evaluation set
→ identify stable / easy cases
→ replace some with deterministic rules or classical ML
→ retain TypeSafe for ambiguous tail
~~~

This can make the semantic layer cheaper and more reproducible while preserving flexibility.

## Evaluation

Typed output guarantees interface shape, not truth.

Maintain labeled fixtures and measure:

- precision / recall per taxonomy where applicable
- calibration / threshold behavior
- changes across question-schema versions
- false positive relations
- false negative relations
- cost per processed record
- latency
- proportion escalated to deeper review

Keep model version, question version, and source hash so errors can be reproduced.
