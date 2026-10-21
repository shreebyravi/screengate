# Decisions, testing and risks

Why ScreenGate is built this way, how it was checked, and what could go wrong.

## Decisions and testing

### Product decisions
| Decision | Why |
|---|---|
| A person always decides; ScreenGate never approves or blocks | The company stays accountable for every payment |
| Three options were weighed: rules only, full automation, AI that recommends while a person decides. The third was chosen | Rules match names but cannot judge or explain; full automation removes accountability |
| Clean payments are not auto-approved | A person should still see and own every decision in a pilot |
| Only payments the payment system flags reach ScreenGate | Analyst time goes where the risk is |
| It checks sanctions and policy risk, not fraud | Keeps the claim honest and the scope testable |
| Two corridors only (UAE-India, UAE-UK) | A narrow scope keeps the pilot small and testable |
| Data is synthetic | A real pilot waits for a privacy and legal review |

### How it was tested
Six test payments, each with the expected result written **before** it was run. The AI was run on each, and a person judged every result. All six passed.

| Test | Situation | Expected | Result |
|---|---|---|---|
| EC-1 | Clean payment | Pass | Pass |
| EC-2 | Missing identity details on a name match | Escalate | Escalate |
| EC-3 | Same name, different person | Pass, citing the differing fields | Pass |
| EC-4 | Receiver bank in a high-risk country | Extra checks | Extra checks |
| EC-5 | Confirmed sanctions match | Escalate | Escalate |
| EC-6 | A politically exposed person signal (outside scope) | Escalate for manual handling | Escalate |

### One improvement
A deliberately hard case (T-1016) matched a watchlist entry only through a weak alias. ScreenGate escalated correctly, but its citation named an alias that was not in the payment data. The instructions were tightened so it cites only the field that actually matched, and the case was re-tested: the decision stayed Escalate and the citation became correct.

### What was learned
Hard cases teach more than clean ones. Writing the expected result first keeps the judging honest.

### Known limits
Name matching relies on the AI's own judgment and was tested on six cases plus one hard case. English names only. Decisions are not saved after a page reload. List coverage is outside its scope.

## Risks and privacy

### Main risks
| Risk | Why it matters | Mitigation |
|---|---|---|
| A missed escalation | The most serious error: a true match is cleared | Hard zero in the metrics; weekly sample review; pause on any breach |
| Analysts over-trusting the recommendation | A person stops checking | Evidence shown with every result; accepted-unchanged and edited rates monitored |
| Incomplete watchlist | ScreenGate inherits the gap | Out of scope and stated; list coverage is the company's control |
| Model or instruction drift | Behaviour changes without notice | The six tests re-run monthly and after any change |
| Personal data sent to an AI provider | Sensitive, regulated data | Synthetic data only until a formal privacy and legal review |

### Privacy
The AI receives the payment record (receiver name, receiver's bank, amount, countries, history), the receiver's profile (date of birth or incorporation, ID number, address), and the sanctions list, country risk list and policy. This goes to the AI provider to produce a recommendation. The prototype saves nothing after a page reload. In a real pilot only the product owner and compliance reviewers would see logs.

A real pilot needs a formal privacy and legal review first. It would cover, for example: the UAE Personal Data Protection Law (Federal Decree-Law 45 of 2021) and DIFC or ADGM rules where relevant; UK GDPR and the Data Protection Act 2018; India's Digital Personal Data Protection Act 2023; cross-border transfer to an AI provider and that provider's terms; and the company's anti-money-laundering record-keeping rules. Legal counsel confirms which apply.

In the live demo each visitor's AI key stays in their own browser and is never stored on or sent to this site. All data in this repository is synthetic.
