# Graph, grounding, and claim provenance

## Graph-first model

Represent important knowledge as semantic triples:

~~~text
subject → predicate → object
~~~

A triple is not sufficient by itself. Attach qualifiers that make the statement auditable and temporally meaningful.

Recommended fields:

~~~yaml
triple_id: t_123
subject_id: company_42
predicate: has_open_role
object_id: role_987
qualifiers:
  observed_at: 2026-09-18
  geography: global
provenance:
  source_record_id: src_456
  source_url: https://example.com/...
  retrieved_at: 2026-09-18T08:00:00Z
method:
  type: observed
  version: parser_v2
confidence: high
~~~

For a derived value:

~~~yaml
claim_id: c_991
subject_id: company_42
predicate: engineering_hiring_share
object: 0.64
qualifiers:
  observed_at: 2026-09-18
provenance:
  source_record_ids:
    - src_1
    - src_2
method:
  type: derived
  calculation_id: calc_engineering_share_v3
confidence: high
~~~

For an inferred value, record model / method and uncertainty.

## Observed vs derived vs inferred

### Observed

Directly supplied by a source.

Examples:

- job title from a company careers page
- reported funding amount
- model download count returned by an API
- wave forecast returned by a marine source

### Derived

Deterministic computation over observations.

Examples:

- engineering jobs / all jobs
- 90-day job-count growth
- funding per employee estimate when both inputs are fixed observations
- average predicted wave height over a time window

### Inferred

A model or semantic decision.

Examples:

- job belongs to AI-agent engineering
- beach visibility likely falls in a range
- company has meaningful healthcare-AI focus
- product positioning shifted toward enterprise buyers

Inference requires explicit method, confidence, and limitations.

## NLP grounding rules

Use NLP to:

- recover structure from unstructured text
- identify candidate entities
- map labels to taxonomies
- judge whether candidate relations are supported
- cluster query language
- verbalize validated structured findings

Do not use NLP as the sole basis for:

- numeric facts
- causal claims
- unsupported classifications
- invented relationships
- time-series trends without observations
- rankings whose metric definition is unclear

Prefer **candidate extraction + selection / verification** to open-ended generation.

Example:

1. deterministic parser extracts candidate role title, department, location, and description;
2. taxonomy contains allowed job functions;
3. semantic model chooses the best matching function with probabilities;
4. stored semantic feature becomes a reusable graph edge;
5. aggregate code computes hiring mix.

## Claim ledger

Every factual sentence in a scaled page should map to one or more claim IDs.

A renderer can receive:

~~~json
{
  "claims": [
    {
      "id": "c_123",
      "metric": "engineering_hiring_share",
      "value": 0.64,
      "display": "64%",
      "observed_at": "2026-09-18",
      "status": "derived",
      "confidence": "high"
    }
  ]
}
~~~

The rendering layer may produce:

> 64% of the company’s currently observed openings are engineering roles.

It may not silently produce:

> The company is aggressively betting its future on engineering.

The second statement adds interpretation, motive, and directionality that the claim does not prove.

## Temporal triples

For changing facts, prefer append-only observations over overwriting values.

Instead of:

~~~text
company → open_job_count → 37
~~~

store:

~~~text
company → open_job_count → 29  [observed_at=2026-08-18]
company → open_job_count → 37  [observed_at=2026-09-18]
~~~

Then deterministic code can compute:

- absolute change
- percent change
- rolling averages
- acceleration / deceleration
- cohort percentiles

Do not ask a language model to infer a numeric trend that code can calculate.

## Entity resolution

Bad entity resolution poisons every downstream computation.

For each entity class define:

- stable internal ID
- canonical name
- aliases
- source-specific IDs
- canonical URLs / domains
- geography where needed
- merge / split rules
- confidence and human-review state

Do not merge entities based only on a similar name.

## Comparability

Before computing rankings or differences, ask whether the observation process is comparable.

Examples:

- public GitHub activity is not equivalent across companies that publish different amounts of code;
- job counts differ when careers systems expose duplicates or evergreen openings;
- crime data differs when jurisdictions use different definitions;
- weather stations differ in siting and coverage.

A mathematically correct formula can still produce a misleading claim.

When comparability is weak:

- narrow the cohort;
- normalize carefully;
- disclose limitations;
- avoid the ranking;
- present raw dimensions separately.

## Named metrics

Named metrics can become citation-worthy concepts, but only when they represent a clear calculation.

Good metric design:

- answers a real question;
- uses interpretable inputs;
- has a stable formula;
- is reproducible;
- exposes method and freshness;
- represents uncertainty when inferred.

Avoid arbitrary “magic scores.”

Prefer separate dimensions when a single score would hide major assumptions.

## Rendering from the graph

Page generation should look like:

~~~text
subgraph
+ computed metrics
+ claim ledger
+ presentation rules
→ HTML / JSON-LD / charts / tables
~~~

not:

~~~text
entity name
+ prompt
→ free-written page
~~~

The language layer should be constrained by available claims.

## Validation

Build fixtures for:

- correct entity merges
- incorrect merge near-misses
- missing source values
- changed source schemas
- ambiguous taxonomy mappings
- low-confidence semantic judgments
- non-comparable cohort members
- stale observations
- contradictory sources

Tests should distinguish:

- source failure
- extraction failure
- entity-resolution failure
- semantic-model error
- calculation bug
- rendering / grounding bug
