---
name: computed-knowledge-seo
description: Build SEO and AEO data products that create novel, defensible facts by joining multiple datasets, grounding semantic relationships, computing derived metrics, and publishing useful answers that generic LLM content cannot substitute. Use when designing programmatic SEO, data-led content, AI-search citation strategies, directories that need more dimensionality, or research pages powered by structured data.
license: MIT
---

# Computed Knowledge SEO

## Purpose

Use this skill to create search assets whose value comes from **new knowledge**, not from rewriting information that already exists.

Core principle:

> **Do not publish information an LLM can already synthesize. Publish computed facts it cannot know until you create them.**

Computed Knowledge SEO is primarily a data-product strategy. Pages, charts, calculators, APIs, comparisons, research reports, and AI citations are interfaces over the underlying knowledge asset.

The canonical pipeline is:

~~~text
Question
→ independent data sources
→ entity resolution
→ normalization
→ grounded semantic relationships
→ deterministic joins and calculations
→ inference with explicit uncertainty
→ historical snapshots
→ validated claims
→ pages / tools / APIs / research
→ refresh
~~~

## Non-negotiable rules

### 1. Reject one-dimensional scaled content

A page must not exist merely because one row has a different company, city, job, product, beach, or category.

Weak pattern:

~~~text
row
→ static attributes
→ templated description
→ page
~~~

Strong pattern:

~~~text
entities
→ relationships
→ multiple independent signals
→ computation / comparison / change over time
→ useful finding
→ page
~~~

Adding more columns does not automatically add information gain. Added dimensions must change what can be known, compared, inferred, or decided.

### 2. Graph before prose

Model important knowledge as grounded semantic relationships:

~~~text
subject → predicate → object
~~~

Examples:

~~~text
company → has_open_role → job
company → released_model → model
company → operates_in → healthcare_ai
beach → exposed_to → northwest_swell
forecast → predicts_wave_height → 0.6m
~~~

Attach qualifiers where relevant:

- observed_at
- valid_from / valid_to
- source_id
- source_url
- retrieved_at
- geography
- confidence
- method_version
- calculation_id

Pages are views over validated subgraphs. They are not the source of truth.

Read **references/GRAPH-AND-GROUNDING.md** when designing the data model, claim ledger, provenance rules, or NLP extraction layer.

### 3. No LLM slop

LLMs may help with:

- entity extraction and resolution suggestions
- relation extraction
- taxonomy mapping
- query clustering
- classification
- rendering validated claims into natural language
- writing ingestion, computation, template, and testing code
- drafting bespoke editorial content grounded in evidence

LLMs must not be the factual authority for:

- numeric values
- unsupported relationships
- invented trends
- causal claims
- arbitrary scores or rankings
- generic filler added only to lengthen a page

For scaled output, prefer:

> **Have the LLM write the system that writes the pages, not the pages themselves.**

The application should render from structured data, grounded semantic features, transparent calculations, and reusable templates.

### 4. Claims before paragraphs

Maintain a claim ledger. Every publishable factual statement should trace to source observations, semantic judgments, or deterministic calculations.

A good claim record includes:

- claim ID
- subject
- predicate / metric
- object / value
- time and geography
- provenance
- calculation or method version
- observed vs inferred status
- confidence / uncertainty where applicable

Natural-language rendering may restate a validated claim, but it must not embellish it into a stronger interpretation unless that interpretation has its own rule and evidence.

### 5. Use code for numbers; semantic AI for meaning

SQL, Rust, Python, or other deterministic code should own:

- exact joins
- arithmetic
- unit conversion
- aggregation
- cohort calculations
- time-series analysis
- deterministic rankings
- reproducible metric generation

Semantic AI should be used where ordinary code lacks common-sense language understanding:

- classification
- taxonomy mapping
- bounded relevance judgments
- candidate relation verification
- evidence selection
- claim checking
- ambiguous routing

When TypeSafe AI is available or appropriate, read **references/TYPESAFE-AI.md** and use it as a typed semantic-compute layer rather than a replacement for deterministic code.

### 6. Snapshot changing sources

A public source usually tells you what exists now. Your snapshot history can tell you what changed.

Persist changing observations such as:

- prices
- job counts and job categories
- GitHub stars / contributors / releases
- model counts and downloads
- funding events
- product features
- rankings
- environmental conditions
- search demand

Historical state can become proprietary even when every original source is public.

### 7. Represent uncertainty honestly

Do not present inferred/modelled outputs as observed facts.

Prefer:

~~~text
central estimate
+ plausible range
+ confidence
+ method
+ freshness
+ limitations
~~~

Avoid false precision.

### 8. Scale discoveries, not URLs

Before generating a scalable page type, ask:

> **What new fact, comparison, trend, or decision does this page expose?**

If the answer is only “another record exists,” do not scale it yet.

## Two publishing modes

### Mode A — Scaled computed pages

Use for repeated entity, category, location, comparison, and time-series surfaces.

The LLM should primarily help create:

- data ingestion code
- normalization rules
- entity-resolution workflows
- semantic classifiers / extractors
- SQL and application aggregations
- rendering templates / components
- schema markup
- internal-linking rules
- tests and validation
- claim-verification logic

The production page should be generated from validated structured knowledge.

Do not ask an LLM to independently free-write thousands of pages.

### Mode B — One-off editorial / research pages

Use bespoke prose when:

- keyword demand supports the topic;
- the query is strategically important even without large volume;
- the analysis requires a narrative;
- the site has a genuinely differentiated answer.

For search-led editorial work, treat demand as another dataset. Use Google Ads Keyword Planner / Google Ads API historical metrics when available.

Read **references/KEYWORD-DEMAND.md** for the editorial workflow.

Example:

Question: “What are the best times to snorkel?”

Do not answer with generic prose. Validate demand and query variants, then ground the article in data such as:

- seasonality
- wind
- tides
- wave exposure
- rainfall / runoff
- water temperature
- measured or modelled visibility
- local geography

The article should explain what the data shows and where the answer varies.

## Opportunity discovery workflow

### Step 1 — Start from valuable questions

Look for questions where the answer requires multiple facts.

Good:

- Is hiring a receptionist cheaper than losing missed calls?
- Which AI companies are increasing agent-engineering hiring fastest?
- When is snorkelling likely to have the clearest water at this location?
- Which neighborhoods combine low flood risk with short commutes and affordable housing?

Weak:

- What is an answering service?
- What is AI?
- What is snorkelling?

### Step 2 — Inventory independent data sources

For each question, identify:

- source
- entity key
- geography
- time coverage
- update frequency
- licensing / usage constraints
- observed vs modelled status
- known biases or missingness

Prefer independent signals over multiple copies of the same upstream source.

### Step 3 — Define the common entity model

Examples:

- AI company × time
- beach × forecast period
- city × occupation × month
- property × hazard × year
- company × job family × observation date

Resolve IDs before computing metrics.

### Step 4 — Specify derived metrics before implementation

For every proposed metric, write:

- user question it answers
- input fields
- formula / decision rule
- unit
- aggregation level
- comparison cohort
- refresh cadence
- assumptions
- uncertainty
- failure modes

If the metric cannot be defined clearly, do not publish it.

### Step 5 — Separate observed, derived, and inferred facts

Use three classes:

**Observed** — directly present in a source.

**Derived** — deterministic transformation of observed inputs.

**Inferred** — modelled estimate or semantic judgment with uncertainty.

Do not blur them.

### Step 6 — Build temporal storage

Do not overwrite changing values unless history is genuinely irrelevant.

Store observation time and retrieval time separately when useful.

### Step 7 — Create page families from questions, not database tables

Potential surfaces:

- entity pages
- category × location intersections
- comparisons
- trend pages
- rankings based on transparent metrics
- calculators
- research reports
- atomic metric / data pages
- API or downloadable data

A page family should map to a distinct information need.

### Step 8 — Design atomic citation-worthy facts

Prefer concise, addressable claims such as:

> 61% of the company’s observed open roles were commercial roles on the latest snapshot.

over generic statements such as:

> The company has a strong commercial focus.

Where useful, expose methodology, source dates, and calculation definitions near the fact.

### Step 9 — Validate before scaling

For a sample of entities/pages:

- manually inspect source resolution
- validate formulas
- test semantic classifiers
- check comparability
- inspect generated wording
- verify provenance
- test stale/missing data behavior
- ensure uncertainty is visible
- ensure each page has meaningful information gain

### Step 10 — Refresh and learn

Track:

- organic impressions / clicks
- AI referrals / citations where measurable
- indexation
- links earned
- user engagement with data modules
- source failures
- semantic classification errors
- metric drift
- keyword demand changes

Use first-party observations to improve the dataset over time.

## Information-gain ladder

Prefer opportunities further down this ladder when they remain valid and useful:

1. **Collect** — gather sources.
2. **Normalize** — make them comparable.
3. **Join** — connect independent datasets.
4. **Calculate** — create a new metric.
5. **Infer** — estimate something not directly observed.
6. **Model** — answer scenarios or decisions.
7. **Observe** — add first-party outcomes / history that competitors cannot easily reproduce.

A large collection is not automatically a moat. The strongest assets typically combine several levels.

## Quality gates

Do not scale a page type unless it passes these tests.

### Novelty
Does it expose a fact, relationship, trend, estimate, or comparison the source datasets do not directly state?

### Utility
Would a real searcher, analyst, buyer, traveler, investor, operator, or AI assistant have reason to ask for it?

### Validity
Do the inputs logically support the output?

### Comparability
Are measurements genuinely comparable across entities?

### Provenance
Can the result be traced to sources and methods?

### Uncertainty
If modelled, is uncertainty represented honestly?

### Distinctiveness
Would a generic LLM need this dataset or analysis to reproduce the answer accurately?

### Maintainability
Can the source, metric, and rendering pipeline be refreshed reproducibly?

If several gates fail, do not scale.

## Anti-patterns

Reject:

- database row → unique URL → generic description
- 1,000 nearly identical city/company/job pages with no new computation
- multiple columns presented as “multidimensional” when they do not interact
- opaque 0–100 scores with arbitrary weights
- rankings built from non-comparable measurements
- LLM-generated facts
- prose written before the data model
- causal language inferred from correlation
- stale snapshots presented as current
- one-off model calls repeated on every page render
- pages whose only differentiation is wording

## Real-world pattern tests

Read **references/CASE-STUDIES.md** for the full examples.

Use these shorthand tests:

1. **Walk Score test — Is there a new fact?**
2. **NeighborhoodScout test — Is entity resolution part of the value?**
3. **First Street test — Does the output answer the real user decision?**
4. **Niche test — Can the moat deepen through first-party data or history?**
5. **NextBurb test — Would the page exist only because another row exists?**
6. **Graphiq test — Is the knowledge graph broad but generic?**
7. **GreatSchools test — Are assumptions hidden inside a magic score?**
8. **CrimeGrade test — Are the compared measurements genuinely comparable?**
9. **Zestimate test — Is model uncertainty visible?**

## Example — AI company intelligence

Weak product:

> Directory of AI companies with name, description, industry, funding, and location.

Computed Knowledge product:

~~~text
company registry
+ company websites
+ GitHub
+ Hugging Face
+ job listings
+ funding
+ research papers
+ pricing/product pages
+ historical snapshots
→ resolved company-time graph
→ derived signals
~~~

Potential derived signals:

- engineering roles as share of open roles
- hiring growth over 30 / 90 / 365 days
- model release frequency
- GitHub contributor growth
- research output per employee estimate
- funding per employee estimate
- model-to-software activity ratio
- category expansion
- geographic hiring expansion
- pricing changes
- research-to-product activity

The value proposition becomes:

> **A continuously computed intelligence layer over the AI-company ecosystem.**

## Example — snorkelling intelligence

Weak product:

> Generic destination pages describing beaches and average weather.

Computed product:

~~~text
marine forecast
+ wind
+ wave exposure
+ rainfall / runoff
+ tides
+ seasonality
+ local geography
+ observed visibility where available
→ location × time suitability and water-clarity estimates
~~~

The output is valuable because no individual source directly answers the final question.

## Output format for strategy tasks

When asked to design a Computed Knowledge SEO opportunity, return:

1. **User questions worth owning**
2. **Independent datasets**
3. **Common entity model**
4. **Grounded semantic relationships**
5. **Derived metrics / inferences**
6. **Temporal snapshot plan**
7. **Uncertainty / comparability risks**
8. **Page and tool surfaces**
9. **Keyword-demand validation plan**
10. **LLM vs deterministic-code boundary**
11. **Provenance / claim-ledger design**
12. **Validation and refresh plan**
13. **What not to build**

Prioritize a small number of high-information surfaces over a huge thin page count.

## Final doctrine

> **Compute, do not summarize.**

> **Graph before prose. Claims before paragraphs. Computation before commentary.**

> **Use NLP to structure and communicate evidence, not to manufacture evidence.**

> **For scaled output, have the LLM write the system that writes the pages, not the pages themselves.**

> **Scale discoveries, not URLs.**

The goal is not to produce more content than an LLM.

The goal is to become a **source the LLM needs**.
