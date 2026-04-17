# Heilmeier Catechism — Reference Guide

The Heilmeier Catechism was developed by George H. Heilmeier (former DARPA director) as a standard for evaluating research and product proposals. It forces specificity and eliminates hand-waving.

## The 9 Questions

**1. What are you trying to do?**
Articulate objectives in plain language. No jargon. If you cannot explain it to a curious non-expert, your problem definition is not clear enough.

**2. How is it done today, and what are the limits of current practice?**
Name the specific alternatives: competitors, workarounds, manual processes. Be precise about their limits — not "it's hard" but "it requires X weeks of engineering and misses Y% of cases."

**3. What is new in your approach and why do you think it will be successful?**
The "why us, why now" question. Name 2-3 specific advantages vs. alternatives. If you cannot articulate a durable advantage, the moat is weak.

**4. Who cares?**
Name specific roles (CISO, DPO, ML Platform Lead) and/or segments. "Everyone" is not an answer. Identify the economic buyer and the champion separately if they differ.

**5. If you succeed, what difference will it make?**
Quantify the delta: revenue, accounts unblocked, time saved, risk reduced. Link to a company metric (ARR, AFGR, attach rate). If you cannot quantify, state the qualitative shift precisely.

**6. What are the risks?**
Use a table: Risk | Likelihood | Mitigation. Include competitive risk. Include "we are wrong about the problem" as a row. Avoid generic risks — be specific to this feature.

**7. How much will it cost?**
Eng-weeks for MVP. Full program budget if multi-quarter. State assumptions. If uncertain, give a range.

**8. How long will it take?**
Milestone table with dates. Include beta and GA separately. Do not compress to "6 months" — show the shape of the work.

**9. What are the midterm and final "exams" to check for success?**
Binary pass/fail criteria. Observable from outside the team. Mid-term = beta milestone. Final = GA success. No subjective measures.

## Common Failure Modes

- **Q1 is jargon-heavy** → rewrite in terms of customer pain, not product features
- **Q2 dismisses alternatives** → alternatives need a fair description or reviewers won't trust your analysis
- **Q3 lists features, not advantages** → name why the feature creates a moat, not what it does
- **Q9 is vague** → "customers are happy" is not an exam; "NPS ≥ 8 in 3 of 5 beta accounts" is
