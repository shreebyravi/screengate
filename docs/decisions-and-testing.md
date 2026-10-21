# Decisions and testing

## Product decisions
| Decision | Why |
|---|---|
| A person always decides; ScreenGate never approves or blocks | The company stays accountable for every payment |
| Three options were weighed: rules only, full automation, AI that recommends while a person decides. The third was chosen | Rules match names but cannot judge or explain; full automation removes accountability |
| Clean payments are not auto-approved | A person should still see and own every decision in a pilot |
| Only payments the payment system flags reach ScreenGate | Analyst time goes where the risk is |
| It checks sanctions and policy risk, not fraud | Keeps the claim honest and the scope testable |
| Two corridors only (UAE-India, UAE-UK) | A narrow scope keeps the pilot small and testable |
| Data is synthetic | A real pilot waits for a privacy and legal review |

## How it was tested
Six test payments, each with the expected result written **before** it was run. The AI was run on each, and a person judged every result. All six passed.

| Test | Situation | Expected | Result |
|---|---|---|---|
| EC-1 | Clean payment | Pass | Pass |
| EC-2 | Missing identity details on a name match | Escalate | Escalate |
| EC-3 | Same name, different person | Pass, citing the differing fields | Pass |
| EC-4 | Receiver bank in a high-risk country | Extra checks | Extra checks |
| EC-5 | Confirmed sanctions match | Escalate | Escalate |
| EC-6 | A politically exposed person signal (outside scope) | Escalate for manual handling | Escalate |

## One improvement
A deliberately hard case (T-1016) matched a watchlist entry only through a weak alias. ScreenGate escalated correctly, but its citation named an alias that was not in the payment data. The instructions were tightened so it cites only the field that actually matched, and the case was re-tested: the decision stayed Escalate and the citation became correct.

## What was learned
Hard cases teach more than clean ones. Writing the expected result first keeps the judging honest.

## Known limits
Name matching relies on the AI's own judgment and was tested on six cases plus one hard case. English names only. Decisions are not saved after a page reload. List coverage is outside its scope.
