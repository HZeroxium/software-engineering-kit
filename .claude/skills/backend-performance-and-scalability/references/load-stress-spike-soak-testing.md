# Load, Stress, Spike, and Soak Testing

## Load Test

Expected traffic under normal or peak conditions.

## Stress Test

Push beyond expected capacity to find breaking point.

## Spike Test

Sudden traffic increase to test elasticity and queue behavior.

## Soak Test

Long-duration test to find leaks, degradation, or saturation.

## Test Design Questions

- What hypothesis is being tested?
- What traffic shape is realistic?
- What environment is safe?
- What data cleanup is required?
- What metrics determine pass/fail?
- What alerts may fire?

## Safety

Never run high-load tests against shared or production systems without explicit approval.
