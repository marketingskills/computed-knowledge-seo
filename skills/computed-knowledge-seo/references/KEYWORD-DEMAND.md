# Keyword demand and one-off editorial pages

## Purpose

Computed Knowledge SEO does not require every useful finding to have measurable keyword volume. However, bespoke editorial work has an opportunity cost.

Use search-demand data to decide which one-off pages deserve custom analysis and prose.

Treat **search demand as another dataset**, not as truth.

## Preferred source

When available, use Google Ads Keyword Planner / Google Ads API historical metrics to validate:

- query wording
- approximate demand
- seasonality
- geography
- related query variants
- commercial value signals

Useful fields to retain include:

~~~text
keyword
avg_monthly_searches
monthly_search_volumes
competition
competition_index
top_of_page_bid_low
top_of_page_bid_high
geo
language
retrieved_at
~~~

Historical keyword metrics update over time, so store retrieval date and cache responsibly.

## Editorial workflow

### 1. Start with a real question

Example:

> What are the best times to snorkel?

### 2. Expand likely query language

Examples:

- best time to snorkel
- best time of day to snorkel
- best month to snorkel in [destination]
- morning vs afternoon snorkeling
- best tide for snorkeling
- clearest water time of day

Use Keyword Planner to measure actual variants rather than relying on intuition alone.

### 3. Segment intent

Separate:

- broad informational intent
- location-specific intent
- seasonal intent
- conditions / safety intent
- commercial / trip-planning intent

Do not collapse different intents into one page just because keywords are similar.

### 4. Ask whether the site has a differentiated answer

A keyword with volume is not enough.

The page should be able to answer using proprietary or computed knowledge.

For snorkelling:

~~~text
search demand
+ destination seasonality
+ hourly wind climatology / forecast
+ tides
+ wave exposure
+ water temperature
+ rainfall / runoff
+ measured or modelled visibility
→ evidence-backed answer
~~~

### 5. Decide page type

Use a **template/computed page** when the same question repeats across many entities with structured answers.

Use a **bespoke editorial page** when:

- the query is broad and deserves synthesis;
- the answer needs explanation and caveats;
- there is strong demand;
- the page can become a hub linking to computed entity pages.

### 6. Write from the evidence bundle

The LLM may draft the article, but provide it:

- claim ledger
- computed tables
- chart data
- source notes
- methodology
- uncertainty
- approved comparisons
- keyword / intent brief

Do not ask it to fill knowledge gaps from memory when the site’s value proposition is grounded data.

## Demand is not factual evidence

Keyword volume can decide **what to investigate and publish**.

It does not decide:

- which claim is true;
- which company is better;
- when conditions are objectively best;
- whether a relationship is causal.

Those require domain data and transparent computation.

## Search demand can itself become computed knowledge

Interesting opportunities emerge when search demand is joined with market or environmental data.

Examples:

~~~text
AI category search demand growth
+ company formation
+ funding
+ hiring growth
→ categories where buyer interest and industry activity diverge
~~~

~~~text
snorkelling destination search seasonality
+ historical predicted / observed conditions
→ when people search versus when conditions are actually strongest
~~~

This is stronger than using keyword volume only as an editorial planning tool.
