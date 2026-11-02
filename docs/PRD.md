# ScreenGate: Product requirements

| | |
|---|---|
| **Product** | ScreenGate, an AI first pass on flagged cross-border payments |
| **Owner** | Shree Byravi |
| **Status** | Working prototype on synthetic data; not production |
| **Corridors** | UAE-India and UAE-UK |
| **Updated** | 2 November 2026 |

## Summary

ScreenGate helps a compliance analyst make a faster, consistent first pass on a flagged cross-border payment, with the evidence written down. A person makes every final decision.

## Problem

A payment system flags some payments for a sanctions check. An analyst then compares the receiver and bank against watchlists, profiles, country risk and policy, one payment at a time. That is slow, can vary when the team is busy, and is hard to explain afterwards. See [DISCOVERY.md](DISCOVERY.md).

## Users

- **Primary:** the compliance analyst, who reviews every flagged payment.
- **Also involved:** the compliance officer who handles escalations, the head of compliance, the payment-system owner, and privacy and legal.

## Goals and measures

| Goal | Measure | Target, projected until a pilot runs |
|---|---|---|
| Faster review | Median analyst time per flagged payment | At least 40% lower than a measured baseline |
| Useful recommendations | Accepted unchanged | At least 80% |
| Stay safe | Missed escalations; payments released without a person's decision | Zero |

## Scope

**In:** payments the company's payment system has flagged (a new receiver, an amount over $10,000, or a receiver or bank in a high-risk country) on the UAE-India and UAE-UK corridors.

**Out (stays fully manual in a pilot):** other corridors; names in other languages or spellings; payments with a politically exposed or government-linked person, which ScreenGate always escalates; and payments above a ceiling the head of compliance sets before day one.

## Non-goals

- Holding or releasing money
- Detecting fraud
- Fixing watchlist coverage
- Replacing the screening tool, customer due diligence, transaction monitoring or regulatory reporting

## Requirements

### Recommendation

| Recommendation (as shown) | Meaning |
|---|---|
| **Looks clear** (Pass) | No unresolved match or risk signal found |
| **Extra checks needed** (Enhanced Due Diligence) | No name match, but a risk factor such as a high-risk jurisdiction requires more checking |
| **Cannot clear: escalate** (Escalate) | A person above the analyst must handle it |

### Behaviour rules

1. Escalate a **confirmed** watchlist match, whatever the amount or country.
2. Escalate when identity fields needed to confirm or clear a match are **missing**.
3. Clear a name match only when an identity field shows a different party, and cite the differing fields.
4. Require Extra checks for a receiver bank in a **Black-tier** jurisdiction, even with no name match.
5. Escalate signals outside its scope, such as a politically exposed person, for manual handling, without assessing them.
6. Never approve or block a payment, and never claim to detect fraud.

### Screen

7. Show the payment and why the payment system flagged it.
8. Show the recommendation beside the payment title, with findings, cited reasoning and history.
9. Let a person approve, edit or escalate. Escalate asks for a one-line reason.
10. Label each AI result "AI-generated, please verify".
11. Provide recorded examples for visitors without a key, clearly labelled.

## AI trade-offs and decisions

| Decision | This prototype | Trade-off |
|---|---|---|
| Autonomy | ScreenGate recommends; a person decides everything | Accountable, but limits time saved |
| Rules or AI | Written policy, applied through AI judgement | Good for explanations, but name matching is less predictable than a dedicated algorithm |
| Context | Whole small watchlist in every call | Simple, but wouldn't work for a real watchlist |
| Evidence | Six tests and one hard case | Clear learning, but too small to prove reliability |

See [AI_PRODUCT_DECISIONS.md](AI_PRODUCT_DECISIONS.md) for the full set of decisions, what a real implementation would add, and Shree Byravi's role.

## Testing

Six tests were written before they were run, and each result was judged by a person. All six passed. A separate hard case led to one improvement. See [EVALS.md](EVALS.md).

## Dependencies and open questions

- **Dependencies for real use:** payment-system integration, a trusted watchlist, secure key handling or a backend, a saved audit trail, and privacy and legal review.
- **Open questions:** How much time do analysts really spend per payment? Will they trust the reasons? Does ScreenGate add anything to tools the company already has? See [MARKET_SCAN.md](MARKET_SCAN.md).

## Rollout

A conditional go for a small pilot, only after a privacy and legal review and a measured baseline. See [PILOT_AND_MONITORING.md](PILOT_AND_MONITORING.md) and [ROADMAP.md](ROADMAP.md).
