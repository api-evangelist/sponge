---
name: Issue and fund a Sponge Card
description: Onboard an agent to the Sponge Card, create the card, fund it, and read its details.
api: openapi/sponge-openapi-original.json
operations: [getApiSpongeCardStatus, postApiSpongeCardOnboard, postApiSpongeCardTerms, postApiSpongeCardCreateCard, postApiSpongeCardFund, getApiSpongeCardDetails]
method: generated
source: openapi/sponge-openapi-original.json
---

# Issue and fund a Sponge Card

The Sponge Card is a Visa credit card issued by Rain, backed by digital-asset collateral.

## Auth & conventions
- `Authorization: Bearer <SPONGE_API_KEY>` and required `Sponge-Version` header on every request.
- Base URL: `https://api.wallet.paysponge.com`.

## Steps
1. **Check status** — `getApiSpongeCardStatus` (`GET /api/sponge-card/status`) to see whether the agent is onboarded.
2. **Onboard** — `postApiSpongeCardOnboard` (`POST /api/sponge-card/onboard`) with the agent's identity/address.
3. **Accept terms** — `postApiSpongeCardTerms` (`POST /api/sponge-card/terms`).
4. **Create the card** — `postApiSpongeCardCreateCard` (`POST /api/sponge-card/create-card`).
5. **Fund it** — `postApiSpongeCardFund` (`POST /api/sponge-card/fund`) with the collateral amount.
6. **Read details** — `getApiSpongeCardDetails` (`GET /api/sponge-card/details`).

## Notes
- To move funds back out, use `postApiSpongeCardWithdraw` (`POST /api/sponge-card/withdraw`).
- These are physical-consequence operations — see agentic-access/sponge-agentic-access.yml for recommended token TTLs and audit requirements.
