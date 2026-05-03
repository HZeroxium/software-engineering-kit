---
purpose: SLI/SLO/error budget concepts and how they inform symptom-based alert design for backend services
load-when: Designing or reviewing alerts, or evaluating observability maturity for a backend service
tier: domain
see-also: []
---

# SLO and Error Budgets

## Core Concepts

- **SLI** (Service Level Indicator): a measurable signal of service behavior from the user's perspective.
- **SLO** (Service Level Objective): target threshold for an SLI (e.g., availability > 99.9%, p99 latency < 200 ms).
- **Error budget**: the allowed failure margin = 1 − SLO target. A 99.9% SLO gives a ~43-minute/month error budget.
- **Burn rate**: how fast the error budget is being consumed relative to the allowed rate (1× = consuming exactly on pace).

## Common SLIs for Backend Services

| Signal | Typical SLI formula |
|--------|---------------------|
| Availability | `successful_requests / total_requests` |
| Latency | p50 / p95 / p99 request duration |
| Error rate | `failed_requests / total_requests` |
| Throughput | Requests per second (capacity proxy, not user impact directly) |
| Freshness | Age of the most recent successful job/batch output |

Choose SLIs that directly reflect user-experienced quality. Internal resource metrics (CPU, memory, queue depth) are not SLIs.

## How SLOs Inform Alert Design

Alerts should protect the error budget, not react to causes.

**Fast burn** (page immediately):
- Consuming >5% of monthly budget in 1 hour (burn rate ≥ ~36×).
- Short window confirms the signal is real, not noise.
- Use: PagerDuty / on-call escalation.

**Slow burn** (notify, don't page):
- Consuming >10% of monthly budget in 6 hours (burn rate ≥ ~5×).
- Use: ticket, Slack notification, non-urgent follow-up.

Prefer symptom-based alerts (user-visible error rate, latency) over cause-based alerts (CPU > 80%, pod restart count).

## Questions Before Designing an Alert

- What SLI does this alert protect?
- Is the failure user-impacting or internal-only?
- What burn rate threshold justifies an on-call page?
- What is the expected false-positive rate at this threshold?
- Is there a runbook linked from the alert?
- Will this alert stay silent during normal traffic variance?

## Anti-Patterns

- Alerting on causes without tying to user impact (e.g., CPU alert with no latency or error-rate correlation).
- Thresholds too tight → alert fatigue → on-call ignores alerts.
- No SLO defined → no principled way to judge whether an alert threshold is correct.
- Alert fires but team has no visibility into remaining error budget.
- Multiple alerts for the same incident with no deduplication.
