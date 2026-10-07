Decision models handle repeated classification, scoring, and routing tasks in go-to-market workflows. A September 2026 newsletter describes TypeSafe's Jev as a model that returns bounded answers and confidence values, allowing research, qualification, and writing to run as separate steps. The useful pattern is to define clear criteria, evaluate decisions on labeled examples, and route uncertain cases for review before spending more on enrichment or outreach.

# Decision models for GTM

## What the Jev clipping describes

Alex Lindahl's September 28, 2026 article describes three question types. Choice selects from up to 255 options and returns option probabilities and confidence. Score uses 2 to 10 defined levels and returns a weighted average, which can be fractional. Noul returns a probability for a yes/no question. Several questions can share one input, called `state`.

The source positions Jev for persona classification, ideal-customer-profile scoring, buying-signal detection, industry categorization, and reply routing. It does not describe a writing or web-research tool. These are dated source descriptions, not independently tested product capabilities.

## Separate research, decisions, and writing

The article proposes a division of work:

- Use formulas or lookups for deterministic checks such as employee-count thresholds.
- Use research tools to collect missing evidence.
- Use a decision model when judgment must produce a label, score, or probability.
- Generate outreach only for records that pass qualification.

This extends [[ai-marketing-automation-workflows]] by making qualification an explicit gate before downstream spending. It also complements [[cold-email-deliverability-2026]] because selecting recipients is a separate problem from drafting messages or delivering them.

## Define decisions before scaling

Keep input short and labeled, containing only evidence relevant to the question. Write distinct criteria and include an `unclear` option so missing data does not force a substantive classification. Inspect the distribution across options when mistakes occur, then test whether revised criteria improve results.

The source suggests trying 50 rows and manually labeling 20 before running thousands. That is a preliminary check, not enough evidence to establish reliable calibration. For a production workflow, this wiki's inference is to use representative labeled cases and measure errors for each action and confidence range. A reported confidence of 0.9 should not be treated as a proven 90% success rate on a new task.

The clipping gives illustrative routing thresholds of at least 0.90 for automatic action, 0.70 to below 0.90 for review, and below 0.70 for more research or no action. These are examples to evaluate, not universal settings. The cost of a wrong decision should determine the threshold.

## Integration described in September 2026

The article uses a Clay HTTP API column because it reports no native integration at publication. It sends a POST to `https://api.typesafe.ai/v1/systemone` with bearer authentication, model `jev-latest`, a `state`, and a `questions` object. Separate columns extract the chosen persona, confidence, and ICP score. Run conditions skip incomplete rows and gate later enrichment or writing.

Keep merged fields valid JSON. The article describes malformed requests as a likely cause of 422 errors, rate limits as 429, and overload as 529. These API details are retained as source context and require current documentation before implementation.

## Claims and gaps

The newsletter repeats TypeSafe's claims of 193 times faster and 445 times cheaper operation, while noting that these are vendor tests at the high end of claimed real-world gains. Its description of hallucination being impossible only means the output is restricted to allowed options. A model can still select the wrong option. The clipping also reports a 64k-token context cap and warns that adding irrelevant context can reduce accuracy.

At the article's quoted $0.042 per million input tokens, 300 input tokens per row yields $1.26 for 100,000 rows. The arithmetic is consistent, but it is a dated input-token estimate, not a verified total workflow cost. The source leaves explicit placeholders for the comparison with Clay AI columns and whether bring-your-own-key HTTP columns incur Clay charges. Those questions remain unresolved. Its broader contrast with LLM output is also the author's framing, not evidence that other model workflows cannot return structured data.

## Source summary

`processed/Jev Decision AI for GTM (what you need to know).md`: Alex Lindahl describes Jev's bounded question types, a Clay research-to-qualification-to-writing workflow, confidence-based routing, and a small initial evaluation. The clipping includes vendor performance claims and unfinished cost comparisons.

## Related

- [[ai-marketing-automation-workflows]]
- [[cold-email-deliverability-2026]]
- [[ai-assisted-market-research-and-validation]]
