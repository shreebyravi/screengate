# ScreenGate: Case study

**In short:** I built a prototype AI first pass on flagged cross-border payments to learn how to scope and test an AI product where mistakes matter. It isn't a new idea, and it hasn't been used by a real analyst. It shows how I approach this kind of product, not proven results.

## My role

I led the product work: the problem, scope, decisions, test cases, verdicts and pilot plan. An AI coding assistant wrote the code from those decisions.

## The problem

When a payment is flagged, an analyst compares the receiver and bank with watchlists, profiles, country risk and policy, one payment at a time. It can be slow, can vary when a team is busy, and can be hard to explain later. How much time this takes is an assumption, to be measured with a baseline.

## Key decisions

| Decision | Why | What it cost |
|---|---|---|
| AI recommends; a person decides | The company stays accountable | Less time saved |
| Only flagged payments reach ScreenGate | Analyst time goes where the risk is | It depends on the payment system's flags |
| Two corridors only | A narrow scope keeps a pilot small and testable | Limited coverage |
| Escalate instead of guessing | A missed match is the most serious error | More cases reach a person |
| Check sanctions and policy risk, not fraud | Keeps the claim honest | A smaller promise |
| Synthetic data only | No real people or sanctions records | Doesn't prove real-world quality |

## How testing changed the product

| What testing or review found | What I did |
|---|---|
| A reviewer flagged a gap: a sanctions-clean payment can still need escalating | Added a politically exposed person test |
| On a hard case, ScreenGate escalated correctly, but cited an alias that wasn't in the payment data | Tightened the instructions and re-tested |
| A stress test showed the policy can clear a match if one field differs, even with a shared ID | Published the weakness and added a fix to the roadmap |

All six main tests passed. Six stress tests, each run three times, reached the expected final recommendation, but one exposed that weakness.

## What went wrong

- **Early wording overclaimed.** I asked whether the fines I cited were really relevant. They showed why controls matter, but ScreenGate wouldn't have prevented them, so I corrected the claims.
- **The tagline still promised too much.** A later review softened "avoid fines" to describe what it actually does.
- **I implied more difference from existing tools than was fair.** A market scan found vendors already describing AI for reviewing alerts, so the README now says this isn't a new idea.
- **Some technical issues reached real use.** They included a broken pop-up during recording and a missing phone setting, found through testing the real experience.

## Outcome

- A working prototype, with recorded examples anyone can try
- Published tests, stress tests, risks, a market scan and a launch plan
- **No business results:** no analyst or company has used it, and the 40% time saving is only a projection

## What I learned

1. Hard cases teach more than clean ones.
2. Writing expected results first keeps judging honest.
3. A safe answer can hide a weak rule, so check the reasoning as well.
4. Evidence has to match the product's actual scope.
5. Finding existing products changes the honest claim, but doesn't remove the learning.

## What I'd do next

Speak with compliance teams, tighten the clearing rule, measure a baseline, and compare building with buying before any pilot. See the [launch plan](LAUNCH_PLAN.md).
