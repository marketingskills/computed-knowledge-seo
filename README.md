# Computed Knowledge SEO

**Build search visibility by creating facts that did not exist until you computed them.**

Computed Knowledge SEO is an Agent Skill for designing SEO and AEO systems around **novel, defensible knowledge produced from multiple datasets** rather than one-dimensional directories, generic information articles, or LLM-generated filler.

The core idea:

> **Compute, don't summarize. Build a source the LLM needs.**

## Install

Install interactively with the open Agent Skills CLI:

```bash
npx skills add marketingskills/computed-knowledge-seo
```

Install non-interactively:

```bash
npx skills add marketingskills/computed-knowledge-seo --skill computed-knowledge-seo -y
```

Install globally:

```bash
npx skills add marketingskills/computed-knowledge-seo --skill computed-knowledge-seo -g -y
```

List the skill without installing:

```bash
npx skills add marketingskills/computed-knowledge-seo --list
```

The repository follows the open Agent Skills convention, so it can be installed into compatible coding agents supported by the `skills` CLI.

## What the skill teaches

Computed Knowledge SEO treats SEO/AEO as a **data-product problem**:

```text
Question
  ↓
Independent data sources
  ↓
Entity resolution + normalization
  ↓
Grounded semantic triples
  ↓
Deterministic joins + calculations
  ↓
Derived / inferred knowledge
  ↓
Claim ledger + provenance
  ↓
Pages, tools, APIs, charts and research
```

Key rules:

- **No 1D scaled content.** A different database row is not enough reason for a page to exist.
- **No LLM slop.** LLMs should generally write the code/templates that render scaled pages, not free-write every page.
- **Graph before prose.** Model important knowledge as grounded subject → predicate → object relationships.
- **Claims before paragraphs.** Published factual language should trace to source observations or transparent calculations.
- **Use code for numbers.** SQL/Rust/Python own exact joins, arithmetic and time-series calculations.
- **Use semantic AI for meaning.** Tools such as TypeSafe AI can classify, verify relations, map taxonomies and evaluate bounded semantic judgments.
- **Snapshot over time.** Historical observations can become a proprietary dataset even when the original sources are public.
- **Validate editorial demand.** For bespoke one-off articles, use Google Ads Keyword Planner / Google Ads API data to validate demand and query language.
- **Scale discoveries, not URLs.**

## Two publishing modes

### 1. Scaled computed pages

For repeatable entity/location/category pages, the LLM should primarily help build:

- ingestion and normalization code
- semantic extraction/classification
- SQL or application-level aggregations
- rendering templates/components
- schema and internal-linking logic
- claim validation and tests

The live page should then render from validated structured data.

### 2. One-off editorial pages

Bespoke articles can be appropriate when there is real search demand or strategic research value.

Example:

> What are the best times to snorkel?

Use keyword data to validate the opportunity, then answer it from real underlying data such as seasonality, wind, tides, wave exposure, visibility, rainfall/runoff and water temperature rather than generic prose.

## Real-world patterns included

The skill uses positive and cautionary examples including:

- Walk Score
- NeighborhoodScout
- First Street / Flood Factor
- Niche
- CrimeGrade
- GreatSchools
- Zillow Zestimate
- NextBurb
- Graphiq / FindTheBest

They are used as pattern tests rather than copied as templates.

## Repository structure

```text
skills/
  computed-knowledge-seo/
    SKILL.md
    references/
      CASE-STUDIES.md
      GRAPH-AND-GROUNDING.md
      KEYWORD-DEMAND.md
      TYPESAFE-AI.md
LICENSE
README.md
```

## License

MIT. See [LICENSE](./LICENSE).
