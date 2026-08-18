# WhitelistCurator Early Analysis (v2)

On-chain analysis of early participants in the **WhitelistCurator** permissionless allowlist.

**Contract:** [`0xcb0b0531e86a9ac36fa865ca8e3dbccf047fda91`](https://etherscan.io/address/0xcb0b0531e86a9ac36fa865ca8e3dbccf047fda91)

This repository provides multi-tier cleaned and segmented lists of early depositors.  
Version 2 includes significant improvements after an independent audit revealed a large coordinated farm in the original whale list.

---

## What’s included

| File | Description | Size |
|------|-------------|------|
| `data/early_core_soft.csv` | Soft clean (removed large same-second clusters) | 490 |
| `data/early_core_medium.csv` | Medium clean (+ removed possible shells) | 322 |
| `data/early_core_hard.csv` | Hard clean (+ removed large identical profiles) | 258 |
| `data/whales_clean.csv` | Cleaned whale list (90–100 ETH farm removed) | 127 |
| `data/early_core_full_flagged.csv` | Full Early Core with all flags | ~1000 |
| `methodology.md` | Full methodology and limitations | — |

---

## Key improvements in v2

- Switched whale detection from `final_weight` to `max_single_deposit` (high-water mark)
- Explicitly filtered the large 90–100 ETH stepped farm (previously ~456 addresses)
- Added `identical_profile` detection
- Introduced three cleaning tiers (Soft / Medium / Hard) instead of a single list

---

## Cleaning Tiers (Early Core)

| Tier | Rules | Size |
|------|-------|------|
| **Soft** | Remove large same-second clusters (≥ 5) | 490 |
| **Medium** | Soft + remove possible shells | 322 |
| **Hard** | Medium + remove large identical profiles | 258 |

---

## Important limitations

- Only internal contract data was used
- Heuristics are imperfect (especially same-second and profile matching)
- Not perfect sybil resistance — these are starting points of different strictness
- No funding-source or external labeling analysis

See [`methodology.md`](./methodology.md) for full details.

---

## Context

Original request by [@surfcoderepeat](https://x.com/surfcoderepeat/status/2089353275086696565):

> Would be cool if someone does some analysis, removes clear sybils  
> Segment them on the per hour event and multiplier, think first 1000 were most active ct participants  
> and OS the list

---

## License

Public domain / CC0. Use freely.
