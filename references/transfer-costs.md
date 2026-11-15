# BNB Smart Chain — transaction cost reference

Reference snapshot: **2026-11-15**. Gas prices move; treat the gas-price
figures as a snapshot and prefer a live gas tracker when one is available.

## How BSC fees work

- Every BSC transaction pays **gas**, priced in **Gwei** (1 Gwei = 0.000000001
  BNB) and paid in **BNB**.
- Fee formula: **fee (BNB) = gas units used × gas price (Gwei) ÷ 1,000,000,000**.
- BSC pins the EIP-1559 base fee at **0** (BEP-226), so the gas price is
  effectively a payment to the validator that seals the block.
- The validator-enforced minimum gas price is **0.05 Gwei** (in force since
  October 2025, after reductions from 3 Gwei → 1 Gwei → 0.1 Gwei). The
  prevailing spot price is normally at or near that floor; during congestion
  users bid above it and daily averages can be much higher.
- Blocks arrive roughly every **0.45 seconds**, so a normally-priced
  transaction confirms in about a second.

## Typical gas units per action

| Action | Typical gas units | Notes |
|---|---|---|
| Native BNB transfer | **21,000** | Fixed protocol cost for a plain value transfer. |
| BEP-20 token transfer | **50,000–65,000** | 65,000 is the standard explorer estimate; many tokens use less. |
| Token approval (`approve`) | **≈46,000** | Varies slightly by token contract. |
| DEX swap, single hop (e.g. PancakeSwap) | **150,000–250,000** | Depends on the pair, route and pool type. |
| DEX swap, multi-hop | **250,000–400,000+** | Each extra hop adds its own pool interaction. |
| NFT mint / arbitrary contract call | varies widely | No reliable generic figure; simulate the specific call. |

## Worked examples at the snapshot gas price (0.05 Gwei)

BNB price used for USD figures: **$591** (snapshot, 2026-11-15).

| Action | Calculation | Fee in BNB | ≈ USD |
|---|---|---|---|
| Native BNB transfer | 21,000 × 0.05 Gwei | 0.00000105 BNB | $0.0006 |
| BEP-20 token transfer | 65,000 × 0.05 Gwei | 0.00000325 BNB | $0.0019 |
| DEX swap (single hop) | 200,000 × 0.05 Gwei | 0.00001 BNB | $0.0059 |

## Worked examples at a congested gas price (1 Gwei)

| Action | Calculation | Fee in BNB | ≈ USD |
|---|---|---|---|
| Native BNB transfer | 21,000 × 1 Gwei | 0.000021 BNB | $0.012 |
| BEP-20 token transfer | 65,000 × 1 Gwei | 0.000065 BNB | $0.038 |
| DEX swap (single hop) | 200,000 × 1 Gwei | 0.0002 BNB | $0.12 |

## Caveats

- These are **network fees only**. A wallet, aggregator, or exchange service
  may charge its own service fee on top (for example, Binance Wallet applies
  service fees to agent-executed transactions per its fee schedule).
- Gas *used* is only exact after simulation or execution; wallets normally
  estimate with a safety margin and refund the unused portion of the gas
  limit.
- A failed transaction still pays for the gas it consumed up to the point of
  failure.

<!-- USER SLOT — intentionally left empty in this version. -->
