# Risks and privacy

## Main risks
| Risk | Why it matters | Mitigation |
|---|---|---|
| A missed escalation | The most serious error: a true match is cleared | Hard zero in the metrics; weekly sample review; pause on any breach |
| Analysts over-trusting the recommendation | A person stops checking | Evidence shown with every result; accepted-unchanged and edited rates monitored |
| Incomplete watchlist | ScreenGate inherits the gap | Out of scope and stated; list coverage is the company's control |
| Model or instruction drift | Behaviour changes without notice | The six tests re-run monthly and after any change |
| Personal data sent to an AI provider | Sensitive, regulated data | Synthetic data only until a formal privacy and legal review |

## Privacy
The AI receives the payment record (receiver name, receiver's bank, amount, countries, history), the receiver's profile (date of birth or incorporation, ID number, address), and the sanctions list, country risk list and policy. This goes to the AI provider to produce a recommendation. The prototype saves nothing after a page reload. In a real pilot only the product owner and compliance reviewers would see logs.

A real pilot needs a formal privacy and legal review first. It would cover, for example: the UAE Personal Data Protection Law (Federal Decree-Law 45 of 2021) and DIFC or ADGM rules where relevant; UK GDPR and the Data Protection Act 2018; India's Digital Personal Data Protection Act 2023; cross-border transfer to an AI provider and that provider's terms; and the company's anti-money-laundering record-keeping rules. Legal counsel confirms which apply.

In the live demo each visitor's AI key stays in their own browser and is never stored on or sent to this site. All data in this repository is synthetic.
