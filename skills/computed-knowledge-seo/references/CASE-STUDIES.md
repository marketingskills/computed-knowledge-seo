# Real-world pattern and cautionary examples

These examples are not instructions to copy another site’s scoring system. Use them to recognize structural patterns.

## Positive patterns

### Walk Score — create a new address-level fact

**Inputs**

- nearby amenities
- walking routes / distance
- population density
- block length / intersection patterns
- transit information for Transit Score

**Computation**

A location is transformed into an interpretable walkability / transit metric.

**Output**

A new address- and neighborhood-level fact that the upstream mapping and demographic sources do not directly state.

**Lesson**

> A strong computed metric answers a question the raw ingredients do not.

Pattern test:

**Walk Score test — Is there a new fact?**

Sources:
- https://www.walkscore.com/methodology.shtml
- https://www.walkscore.com/transit-score-methodology.shtml

---

### NeighborhoodScout — entity resolution and spatial modelling are part of the product

**Inputs**

- crime data
- Census / demographic data
- economic and housing data
- geographic boundaries
- other public datasets

**Computation**

Records from heterogeneous geographies and agencies are normalized and modelled into neighborhood-level measures.

**Output**

Neighborhood intelligence that is more useful than a pile of agency tables.

**Lesson**

> Entity resolution, normalization, and geography can themselves create substantial information value.

Pattern test:

**NeighborhoodScout test — Is entity resolution part of the value?**

Source:
- https://www.neighborhoodscout.com/about-the-data

---

### First Street / Flood Factor — answer the decision, not the ingredients

**Inputs**

- elevation
- rainfall
- rivers
- tides
- storm surge
- climate projections
- property characteristics

**Computation**

Hazard models estimate property-level risk.

**Output**

“What is this property’s flood / climate risk?” rather than a list of environmental inputs.

**Lesson**

> Compute toward the user’s real decision.

Pattern test:

**First Street test — Does the output answer what the user actually wants to know?**

Source:
- https://help.firststreet.org/hc/en-us/articles/1500000359741-Flood-Model-Methodology-Calculating-property-level-risk

---

### Niche — public data becomes stronger when combined with first-party observations

**Inputs**

- government education data
- outcomes
- costs
- surveys
- user reviews

**Computation**

Normalization and weighting create comparable dimensions and rankings.

**Output**

Entity pages containing information that is increasingly difficult to reproduce as first-party data grows.

**Lesson**

> Public-data joins can bootstrap a product, but proprietary observations and history deepen the moat.

Pattern test:

**Niche test — Can the moat strengthen over time?**

Source:
- https://www.niche.com/k12/rankings/methodology/

---

### CrimeGrade — useful modelling with explicit comparability caveats

**Inputs**

- FBI and local crime data
- geography
- historical data
- demographic / contextual signals

**Computation**

Normalization and modelling create geographically granular crime estimates / grades.

**Output**

A more usable local risk view than raw jurisdiction tables.

**Lesson**

> Modelling can fill gaps, but definitions and reporting processes may still limit comparability.

Pattern test:

**CrimeGrade test — Are the things being compared actually comparable?**

Sources:
- https://crimegrade.org/about-crimegrade-data/
- https://crimegrade.org/why-the-most-precise-crime-metrics-cant-be-compared/

---

### GreatSchools — a powerful named metric with an important warning

**Inputs**

- test results
- growth / progress
- graduation
- college-readiness signals
- state and federal education data

**Computation**

Several measures are combined into a simple rating.

**Output**

An extremely addressable school-quality metric.

**Lesson**

A named computed metric can become highly reusable, but compressing a complex phenomenon into one number can hide assumptions.

Pattern test:

**GreatSchools test — Are assumptions hidden inside a magic score?**

Sources:
- https://www.greatschools.org/gk/about/ratings-methodology/
- https://www.edweek.org/leadership/are-greatschools-ratings-making-segregation-worse/2019/12

## Cautionary patterns

### NextBurb — page count is not information gain

A published case study described a very large programmatic surface built from location and comparison pages.

The important caution is structural, not that the business was a “failure.”

**Failure mode**

~~~text
many location rows
× many templates
→ huge URL count
~~~

without equivalent growth in genuinely new discoveries per page.

**Lesson**

> Do not optimize for rows × templates. Optimize for relationships × calculations.

Pattern test:

**NextBurb test — Would this page exist only because another row exists?**

Source:
- https://www.mayple.com/case-studies/nextburb

---

### Graphiq / FindTheBest — a giant generic knowledge graph can be commoditized

Graphiq / FindTheBest built a very large cross-vertical knowledge graph.

**Failure mode to guard against**

A graph can be enormous while competing on generic factual retrieval, where search engines and foundation-model ecosystems have structural advantages.

**Lesson**

> The moat is not the number of triples. It is domain-specific computed knowledge that answers valuable questions unusually well.

For an AI-company site, do not merely collect:

- founded date
- headquarters
- funding
- description

Own analytical questions such as:

- which companies accelerated agent-engineering hiring?
- which funded startups translate research into public models fastest?
- where is technical hiring expanding geographically?
- how are pricing models changing over time?

Pattern test:

**Graphiq test — Is the graph broad but generic?**

Source:
- https://techcrunch.com/2015/08/11/findthebest-becomes-graphiq/

---

### GreatSchools — the magic-score problem

A single clean score is easy to search, compare, embed, and cite.

But the cleaner the number looks, the easier it is for users to forget the assumptions underneath it.

**Failure mode**

~~~text
many imperfect signals
→ hidden weights
→ one authoritative-looking number
~~~

**Lesson**

Prefer interpretable dimensions when possible.

For example:

~~~text
Developer Adoption: +37% YoY
Open Model Activity: 14 releases / 12m
Research Output: 31 papers / 12m
Technical Hiring: +22% / 90d
~~~

is often safer and more informative than:

~~~text
AI Company Score: 84/100
~~~

If a composite score is necessary, document weights, sensitivity, limitations, and uncertainty.

---

### CrimeGrade — normalization can create false comparability

Even sophisticated normalization cannot erase differences in how source systems define and collect observations.

Equivalent mistake for an AI-company product:

~~~text
Company A public GitHub contributors = 74
Company B public GitHub contributors = 19
therefore Company A has 3.89× greater developer adoption
~~~

That conclusion may fail because the companies expose different proportions of their engineering publicly.

**Lesson**

> Correct arithmetic does not guarantee a valid inference.

---

### Zillow Zestimate — uncertainty should be part of the product

Zillow combines public records, listing data, user-submitted facts, comparable sales, property characteristics, and market signals into an automated valuation.

Zillow explicitly describes Zestimate as an estimate rather than an appraisal and exposes uncertainty through a range.

**Lesson**

> Modelled outputs should look modelled.

Prefer:

~~~text
Estimate: $510k
Likely range: $475k–$548k
Confidence: medium
Method: modelled
Last updated: ...
~~~

over a naked highly precise number.

Pattern test:

**Zestimate test — Is uncertainty visible?**

Source:
- https://www.zillow.com/zestimate/

## Governing contrast

Weak scaled SEO:

~~~text
row
→ template
→ prose
→ page
~~~

Computed Knowledge SEO:

~~~text
entities
→ grounded semantic relationships
→ joins
→ normalization
→ calculations / inference
→ temporal observations
→ validated claims
→ page / tool / API / research
~~~

> **Scale discoveries, not URLs.**
