# ScreenGate: Business case model

A break-even model a company can fill in with its own numbers.

**This isn't a forecast.** There are no real volumes, times, costs or prices here, so it makes no ROI claim. The example numbers are made up to show how the calculation works.

## The question

**How much analyst time would ScreenGate need to save per payment to cover its costs?**

## The calculation

```text
Break-even hours per month = total monthly cost ÷ analyst cost per hour

Break-even minutes per payment = break-even hours × 60 ÷ flagged payments per month
```

## Inputs the company needs

| Input | Source | In this example |
|---|---|---|
| Flagged payments per month | Payment system | 1,000, 5,000 or 20,000, made up |
| Analyst cost per hour | Finance or HR | USD 40, made up |
| Baseline time per payment | Measured on about 20 cases | Not known |
| AI cost | Provider pricing × tokens × payments | Part of the monthly cost |
| Hosting, integration, support and governance | IT, compliance or vendor | Part of the monthly cost |
| One-time build and setup | Project plan | Not included in the example |

**AI cost per payment** = (input tokens × input price) + (output tokens × output price).

## Example only

Break-even time saved per payment, using the made-up inputs above:

| Assumed total monthly cost | Hours to save per month | 1,000 payments | 5,000 payments | 20,000 payments |
|---|---|---|---|---|
| USD 10,000 | 250 | 15 min | 3 min | 0.75 min |
| USD 25,000 | 625 | 37.5 min | 7.5 min | 1.9 min |
| USD 50,000 | 1,250 | 75 min | 15 min | 3.8 min |

**How to read it:** at 5,000 flagged payments and USD 25,000 a month, ScreenGate would need to save about 7.5 analyst minutes per payment. Compare that with the measured baseline. If a payment takes less than that now, the case fails at that volume.

## Build or buy

Vendors already describe AI for reviewing alerts. A real company should compare:

| Compare | Build | Buy |
|---|---|---|
| Quality | Same test set | Same test set |
| Upfront and ongoing cost | Team, hosting and support | Licence and integration |
| Control | High | Depends on the vendor |
| Time to pilot | To be estimated | To be quoted |
| Audit and evidence | Must be built | Check what's included |

We have no vendor prices, so this table has no numbers.

## What the model leaves out

| Possible extra value | Possible extra cost or risk |
|---|---|
| More consistent decisions | Analyst review time still needed |
| Clearer audit evidence | Training and compliance governance |
| Reduced queue during busy periods | Cost of a missed escalation, which can't be offset by time saved |

**Time saved only has financial value if the company uses it,** such as handling more volume without adding staff. A safety failure can outweigh any saving, so zero missed escalations remains a hard limit and isn't traded off here.

## How to validate it

1. Measure the baseline in [discovery](LAUNCH_PLAN.md).
2. Replace every made-up input with company data.
3. Measure time saved and quality during the pilot.
4. Decide at the gate: scale, buy, narrow or stop.
