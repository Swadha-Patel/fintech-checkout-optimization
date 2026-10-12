# Fintech checkout optimization

**By Swadha Patel · Independent product strategy project · Synthetic experiment**

## The question
Does a guest-first checkout improve paid-order completion without weakening payment quality? The dashboard compares a hypothetical account-first control with a guest-first variant, then explores device segments and conditional contribution.

## Explore
Inspect the unique-user funnel from checkout start to completed details, submitted payment, and paid order. Filter by device, read an approximate 95% interval for the completion difference, and test future checkout volume and net contribution per incremental order.

## Data and experiment assumptions
Four synthetic aggregate rows: two devices × two variants. There are 3,000 starting users per arm, with one eligible checkout per user. Assumes stable, independent user-level randomization, 14-day enrollment and complete 30-day refund follow-up. These are educational assumptions, not a real merchant test.

Control: 1,790 / 3,000 completed (59.67%). Guest-first: 1,920 / 3,000 (64%). Absolute difference: 4.33 percentage points; approximate 95% interval: 1.88–6.79 percentage points. Relative completion lift is 7.26%; relative abandonment reduction is 10.74%. These use different denominators. The desktop subgroup interval includes zero.

## Method
For independent proportions p1 and p0, SE = sqrt[p1(1-p1)/n1 + p0(1-p0)/n0]. The displayed interval is (p1-p0) ± 1.96 × SE. This normal approximation assumes adequate counts and a fixed analysis horizon. Segment comparisons are exploratory and not adjusted for multiple comparisons.

Payment success is paid users / submitting users, not transaction-attempt authorization. Refund rate is refunded paid orders / paid orders. Guardrails are descriptive; this sample does not establish non-inferiority.

## Decision and value
The value scenario multiplies completion difference × future starts × assumed net contribution per incremental order. Contribution excludes fixed rollout costs and assumes variable costs, processing fees and expected refunds are already reflected. The interval range propagates only rate uncertainty, not demand or margin uncertainty; it is not a forecast interval. A real rollout needs a pre-specified sample, guardrails, and monitoring. No real conversion or revenue improvement is claimed.

## References
- [Baymard checkout UX research](https://baymard.com/research-articles/current-state-of-checkout-ux)
- [Stripe payment analytics](https://docs.stripe.com/payments/analytics)

These references provide context, not the synthetic observations.

## Run locally

No build step, API keys, or JavaScript dependencies are needed. From the repository folder:

```sh
python3 -m http.server 8000
```

Open http://localhost:8000. You can also open `index.html` directly. Optional hosted fonts fall back to system fonts offline.

## Files

- `index.html`: standalone dashboard entry point
- `dashboards.js`: rendering, filters, scenarios, and methodology panels (shared portfolio renderer)
- `dashboard-math.js`: pure calculations, shared with the portfolio
- `dashboard-data.json` and `dashboard-data.js`: the same illustrative dataset in inspectable and browser-ready forms
- `*-illustrative-data.csv`: inspectable source values
- `test.cjs`: numerical and data-consistency checks, run with `node test.cjs`

The shared renderer contains both portfolio dashboard templates; this repository loads only its own dataset and project view. No data leaves your browser.
