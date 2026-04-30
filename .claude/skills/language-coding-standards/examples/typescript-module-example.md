# TypeScript Module Example

This example is illustrative and not repo-specific.

## Goal

Normalize external API data with runtime checks before using it internally.

## Example

```typescript
export type UserStatus = "ACTIVE" | "DISABLED";

export interface UserSummary {
  id: string;
  displayName: string;
  status: UserStatus;
}

interface RawUserResponse {
  id?: unknown;
  name?: unknown;
  status?: unknown;
}

export function toUserSummary(raw: RawUserResponse): UserSummary {
  if (typeof raw.id !== "string" || raw.id.length === 0) {
    throw new Error("Invalid user id");
  }

  if (typeof raw.name !== "string" || raw.name.length === 0) {
    throw new Error("Invalid user name");
  }

  if (raw.status !== "ACTIVE" && raw.status !== "DISABLED") {
    throw new Error("Invalid user status");
  }

  return {
    id: raw.id,
    displayName: raw.name,
    status: raw.status,
  };
}
```

## Notes

- External input is treated as unknown.
- Runtime validation narrows types.
- Internal UserSummary is stable and explicit.
- Errors are generic and do not leak sensitive external payloads.
- No validation library is introduced because library choice depends on the current repo.
