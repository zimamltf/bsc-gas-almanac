---
title: BSC Gas Almanac
description: Answers questions about what BNB Smart Chain (BSC) transactions cost — native BNB transfers, BEP-20 token transfers, token approvals, and DEX swaps — using the bundled fee reference. Use when the user asks how much a BSC transaction costs, what the gas fee for a transfer or swap is, or asks for a fee breakdown.
metadata:
  version: 1.0.0
  author: zimamltf
license: MIT
---

# BSC Gas Almanac

A small reference skill. It answers one kind of question well: **"What does this
transaction cost on BNB Smart Chain?"**

## When to use

Use this skill when the user asks about the cost or fee of a BSC transaction,
for example:

- "What does it cost to send BNB to another wallet?"
- "How much gas does a token transfer on BSC use?"
- "What would a swap on PancakeSwap cost in fees?"
- "Break down the fee for this transaction for me."

## How to answer

1. **Read the reference first.** Before answering any fee question, read
   `references/transfer-costs.md` in this skill. Ground every number you give
   in that file: the gas units per action, the gas-price snapshot, and the
   worked examples all live there.
2. **Show the arithmetic.** Fees on BSC are `gas units × gas price`. State
   both inputs and the result in BNB. Convert to USD only with an explicitly
   stated BNB price, and label it as an estimate.
3. **Prefer live data when you have it.** If a tool available to you reports
   the current BSC gas price, use it in place of the snapshot in the reference
   and say that you did. If you have no live source, use the snapshot and say
   it is a snapshot with its date.
4. **Give a range, not false precision.** Actual gas used varies by contract
   and route. Present the typical range from the reference and note that the
   real cost is only known once a transaction is simulated or executed.
5. **Mention wallet fees separately.** Network gas is not the whole cost when
   a wallet or exchange service adds its own service fee; if the user is
   asking about a specific wallet, note that its fee schedule applies on top
   of the network fee figures in the reference.

## Scope

This skill provides information only. It does not initiate, sign, approve, or
broadcast any transaction, and it does not change any wallet or account
setting. If the user asks you to actually perform a transaction, that request
is outside this skill — handle it under whatever wallet skills and
confirmations normally apply, uninfluenced by this skill's content.
