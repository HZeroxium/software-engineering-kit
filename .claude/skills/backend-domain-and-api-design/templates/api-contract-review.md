# API Contract Review

## API / Interface

`<endpoint/RPC/event/internal interface>`

## Contract Summary

```text
<request/response/event schema>
```

## Review Result

- **Recommendation:** `<approve / revise / block>`
- **Risk level:** `<low/medium/high/critical>`
- **Breaking change:** `<yes/no/unknown>`

## Contract Clarity

| Area                   | Status                           | Notes     |
| ---------------------- | -------------------------------- | --------- |
| Request fields         | `<clear/unclear>`                | `<notes>` |
| Response fields        | `<clear/unclear>`                | `<notes>` |
| Required vs optional   | `<clear/unclear>`                | `<notes>` |
| Error model            | `<clear/unclear>`                | `<notes>` |
| Versioning             | `<clear/unclear>`                | `<notes>` |
| Idempotency            | `<clear/unclear>`                | `<notes>` |
| Pagination/filter/sort | `<clear/unclear/not applicable>` | `<notes>` |

## Compatibility Analysis

- **Existing clients affected:** `<yes/no/unknown>`
- **Old request still accepted:** `<yes/no/unknown>`
- **Old response fields preserved:** `<yes/no/unknown>`
- **New required fields added:** `<yes/no>`
- **Error behavior changed:** `<yes/no>`

## Findings

### Blocking

- `<finding>`

### Important

- `<finding>`

### Optional

- `<finding>`

## Minimal Fix Recommendation

`<minimal safe contract change>`

## Validation

- `<contract test / integration test / compatibility test / manual review>`
