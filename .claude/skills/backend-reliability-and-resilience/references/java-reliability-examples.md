---
purpose: Illustrative Java code sketches for dependency policy record and fallback shape — for reference only, not copy-paste
load-when: Java code examples explicitly requested for reliability or fallback patterns
tier: scenario
see-also: []
---

# Java Reliability Examples

Examples are illustrative only. Follow repository conventions.

## Dependency Policy Record

```java
public record DependencyPolicy(
    Duration timeout,
    int maxAttempts,
    boolean retryOnlyIfIdempotent
) {}
```

## Fallback Shape

```java
public UserProfileResult getProfile(UserId userId) {
    try {
        return primaryProfileClient.getProfile(userId);
    } catch (DependencyUnavailableException ex) {
        return cachedProfileStore.findFreshEnough(userId)
            .map(UserProfileResult::fromCache)
            .orElseThrow(() -> ex);
    }
}
```

## Notes

- Do not copy without checking data freshness and authorization.
- Retry behavior must match existing internal libraries.
- Fallback must not leak stale or unauthorized data.
