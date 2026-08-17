# WhitelistCurator Early Analysis

On-chain analysis of early participants in the **WhitelistCurator** permissionless allowlist.

**Contract:** [`0xcb0b0531e86a9ac36fa865ca8e3dbccf047fda91`](https://etherscan.io/address/0xcb0b0531e86a9ac36fa865ca8e3dbccf047fda91)

This repository provides segmented and partially cleaned lists of early depositors, following the public request to analyse the list, remove clear sybils, and open-source the results.

---

## What’s included

| File | Description | Rows |
|------|-------------|------|
| `data/early_core_full.csv` | Full Early Core (top 1000 + hours 0–2) with flags | 1 000 |
| `data/early_core_soft_clean.csv` | Early Core without large same-second clusters (≥ 5) | 490 |
| `data/whales_100.csv` | Addresses with final weight ≥ 100 ETH | ~510 |
| `methodology.md` | Full methodology and limitations | — |

---

## Key definitions

**Early Core**  
- Ranked by first deposit time  
- Includes the first 1000 addresses + all addresses from hours 0, 1 and 2

**Flags**
- `possible_shell` — weight < 0.15 ETH and only 1 deposit
- `large_cluster` — 5 or more addresses deposited in the exact same second
- `cluster_size` — size of the same-second group

**Soft Clean**  
Early Core with all `large_cluster = true` addresses removed → **490 addresses**

**Whales**  
Addresses with `final_weight ≥ 100 ETH`

---

## Important limitations

- This is **not** perfect sybil resistance. Only internal contract data was used.
- Same-second clustering is a useful but imperfect signal (organic users can also deposit in the same second during peak attention).
- No funding-source analysis or external wallet labels were applied.
- Lists are snapshots from 17 August 2026.

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
