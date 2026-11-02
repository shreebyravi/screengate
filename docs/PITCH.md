# ScreenGate: A faster first pass on flagged payments, with the evidence written down

**The ask:** 20-30 minutes with someone who reviews sanctions alerts, to tell me what this gets wrong, what your team would need to trust it, and what you'd do differently.

## The problem

When a payment is flagged, an analyst compares the receiver and bank with watchlists, profiles, country risk and policy, one payment at a time. It can be slow, can vary when the team is busy, and can be hard to explain later. Regulators fine firms whose screening controls fail, though ScreenGate wouldn't have prevented those cases by itself.

## What ScreenGate does

- **Starts from evidence, not a blank page:** it recommends Looks clear, Extra checks needed or Cannot clear: escalate.
- **Separates same name from same person:** it compares date of birth, nationality and ID, and cites what it used.
- **Escalates instead of guessing:** confirmed matches, missing identity data and out-of-scope signals go to a person.
- **Leaves the decision with a person:** it never approves or blocks a payment.

## Is this new?

No. Vendors already describe AI for reviewing sanctions alerts, as set out in the [market scan](MARKET_SCAN.md). ScreenGate is a portfolio prototype showing how I'd scope, test and safely pilot this kind of product.

## What exists today

A working prototype on synthetic data, covering UAE-India and UAE-UK payments. It includes six tests and six stress tests with results written down, a documented improvement, and a pilot plan. The stress tests exposed a loose policy rule, which is published too.

**It isn't proven:** no analyst has used it, its name matching was tested on only a few cases, and it isn't production-ready.

## A small, safe next step

| Stage | What happens |
|---|---|
| **Conversation** | Compare the workflow with how your team works |
| **Baseline** | Measure time per payment on about 20 cases |
| **Pilot, if a company chose to run one** | 2 analysts for 6 weeks and about 180 flagged payments, alongside the current process, after a privacy and legal review |

**Projected targets, not results:** at least 40% less analyst time per payment, at least 80% of recommendations accepted unchanged, and zero missed escalations.

## See it

- **Try it, no key needed:** https://shreebyravi.github.io/screengate/recorded-examples/
- **Read the documents:** https://github.com/shreebyravi/screengate
- **Contact Shree Byravi:** https://www.linkedin.com/in/shree-byravi/
