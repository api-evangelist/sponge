---
name: Pay for a paid service with a Sponge wallet
description: Use an agent's Sponge wallet to pay an x402 or MPP endpoint, checking balance first.
api: openapi/sponge-openapi-original.json
operations: [getApiBalances, postApiX402Fetch, postApiMppFetch]
method: generated
source: openapi/sponge-openapi-original.json
---

# Pay for a paid service

Operating instructions for an agent paying a metered/paid endpoint from its Sponge wallet.

## Auth & conventions
- Send `Authorization: Bearer <SPONGE_API_KEY>` (key prefix `sponge_live_` or `sponge_test_`).
- Send the required `Sponge-Version` header on every request (current `0.2.2`).
- Base URL: `https://api.wallet.paysponge.com`.

## Steps
1. **Check funds** — `getApiBalances` (`GET /api/balances`) to confirm the wallet holds enough USDC (x402) or a Tempo asset (MPP).
2. **Pay via x402** — `postApiX402Fetch` (`POST /api/x402/fetch`) to call the target endpoint, paying in USDC over x402.
3. **Or pay via MPP** — `postApiMppFetch` (`POST /api/mpp/fetch`) to call the endpoint over MPP on Tempo (asset negotiated per endpoint, typically USDC.e).

## Notes
- Test keys hide mainnet-only capabilities (e.g. crypto onramp). Use `sponge_test_` keys for sandbox flows.
- No idempotency key is documented; do not blind-retry a payment call.
