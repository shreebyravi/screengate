# ScreenGate: Risk and compliance

**This prototype makes no compliance claim.** It uses only synthetic data and isn't legal advice. Real use needs review by the company's compliance, privacy and legal teams.

## Main risks

| Risk | Why it matters | In the prototype | Before real use |
|---|---|---|---|
| A missed escalation | The most serious error: a true match is cleared | Hard rules and a person's review | Hard zero in the metrics, weekly sample review, and pause on any breach |
| Over-trusting the recommendation | A person stops checking | Evidence shown with every result | Monitor accepted-unchanged and edited rates |
| Incomplete watchlist | ScreenGate inherits the gap | Stated as out of scope | List coverage remains the company's control |
| Model or instruction drift | Behaviour changes without notice | Six repeatable tests | Re-run monthly and after any change |
| Made-up or overclaimed citations | Reasons look credible but aren't | Tightened after T-1016 | Automatic citation checks and sampling |
| Name-matching limits | Other languages and similar names may be mishandled | English names only, stated as a limit | Dedicated matching and wider tests |
| Message or data tries to trick the AI | Text could try to change its behaviour | Small stress test escalated in all runs | Independent security testing |
| Loose clearing rule | Policy Section 3 lets one differing field clear a match, even with a shared ID | The agent still escalated in tests, but through a general instruction | Tighten the rule, and enforce it in code |
| Personal data sent to an AI provider | Sensitive, regulated data | Synthetic data only | Formal privacy and legal review |

## Privacy

The AI receives the payment record (receiver name, receiver's bank, amount, countries and history), the receiver's profile (date of birth or incorporation, ID number and address), and the sanctions list, country risk list and policy. This goes to the AI provider to produce a recommendation. The prototype saves nothing after a page reload. In a real pilot, only the product owner and compliance reviewers would see logs.

A real pilot needs a formal privacy and legal review first. It would cover, for example:

- **UAE:** the Personal Data Protection Law (Federal Decree-Law 45 of 2021), and DIFC or ADGM rules where relevant
- **UK:** UK GDPR and the Data Protection Act 2018
- **India:** the Digital Personal Data Protection Act 2023
- **Cross-border transfer:** sending personal data to an AI provider, and that provider's terms
- **Record-keeping:** the company's anti-money-laundering retention rules

Legal counsel confirms which apply.

In the live demo, each visitor's AI key stays in their own browser and is never stored in this repo or sent to this site.

## What ScreenGate doesn't cover

Watchlist coverage, customer due diligence, transaction monitoring, regulatory reporting, fraud detection, and assessing politically exposed persons, beneficial ownership or adverse media.

## Required before any live use

These can't be written from outside a company, so they aren't included here:

- Security assessment and penetration test
- Data protection impact assessment
- AI vendor and third-party review
- Payment-system integration specification
- Model risk or AI governance review, where the company requires it
- Support runbook, incident process and named sign-offs
