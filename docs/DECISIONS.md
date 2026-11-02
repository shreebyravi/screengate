# ScreenGate: Decision log

Key product decisions and why they were made. Dates are approximate. A later decision replaces an earlier one.

| # | When | Decision | Why | Alternative rejected |
|---|---|---|---|---|
| 1 | Sep 2026 | AI recommends and a person decides | Rules match names but can't judge or explain. Full automation removes accountability | Rules only; full automation |
| 2 | Sep 2026 | Never approve or block a payment | The company stays accountable for every payment | Let ScreenGate act on clean payments |
| 3 | Sep 2026 | Check sanctions and policy risk, not fraud | Keeps the claim honest and the scope testable | Claim wider financial-crime coverage |
| 4 | Sep 2026 | Two corridors only: UAE-India and UAE-UK | A narrow scope keeps a pilot small and testable | Global scope |
| 5 | Sep 2026 | Synthetic data, with regions named Region A, B and C | No real people or sanctions records are used | Real names or records |
| 6 | Sep 2026 | Write expected results before running tests | Keeps the judging honest | Judge results afterwards |
| 7 | Sep 2026 | Add a politically exposed person test | A reviewer flagged a coverage gap: a sanctions-clean payment can still need escalating | Test sanctions cases only |
| 8 | Sep 2026 | Attribute a match only to the field that matched | The T-1016 hard case showed an overclaimed citation | Leave citations as they were |
| 9 | Oct 2026 | Show ScreenGate as one step after a mock payment system | Makes clear that it reviews flagged payments and doesn't replace the system | A standalone checker |
| 10 | Oct 2026 | Only flagged payments reach ScreenGate | Analyst time goes where the risk is | Screen every payment |
| 11 | Oct 2026 | Remove pass-through payments | ScreenGate only sees flagged payments | Keep them in the demo |
| 12 | Oct 2026 | Don't auto-approve clean payments | A person should see and own every decision in a pilot | Automatic clearing |
| 13 | Oct 2026 | Use plain-language labels | Reduces jargon, such as Looks clear instead of OK | Internal technical labels |
| 14 | Oct 2026 | Add recorded examples, clearly labelled | Anyone can try it without a key | Require every visitor to bring a key |
| 15 | Oct 2026 | Six-week pilot with 2 analysts | Long enough to cover a monthly payment cycle, while small and reversible | A shorter, less representative pilot |
| 16 | Oct 2026 | Conditional go | A privacy and legal review and a measured baseline must come first | Unconditional go |
| 17 | Oct 2026 | Say that fines show why controls matter, but ScreenGate wouldn't have prevented them | The cited cases involved list coverage and broad control failures | Imply ScreenGate would prevent such fines |
| 18 | Nov 2026 | State that AI alert review already exists commercially | The market scan found vendors describing similar capabilities | Describe ScreenGate as different from all existing tools |
| 19 | Nov 2026 | Publish the stress tests and the SG-S6 weakness, and leave the policy unchanged for now | Readers should see the limit, and the app's recorded answers came from real runs under this wording | Hide it, or change the policy without re-running the real tests |
