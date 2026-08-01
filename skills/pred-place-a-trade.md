---
name: Place a trade on PRED
description: Authenticate with a wallet signature, enable trading, discover a market, read the orderbook, and place a signed LONG/SHORT order on the Pred sports prediction exchange.
api: openapi/pred-openapi.yml
operations: [loginWithSignature, prepareSafeApproval, executeSafeApproval, getAllParentMarkets, getOrderBook, placeOrder, getPositions]
---

# Place a trade on PRED

PRED is a decentralized, order-book sports prediction exchange settled in USDC on Base. Every order is authorized by an EIP-712 signature from your EOA and executed by your per-user Gnosis Safe proxy wallet.

## Prerequisites
- A partner `X-API-Key` (request from Pred; required only for login).
- An EOA wallet able to produce EIP-712 signatures.
- USDC on Base in your proxy wallet (fund the `proxy_wallet_addr` returned by login).
- Pick an environment first (testnet `https://testnet.pred.app` chain 84532, or mainnet `https://www.pred.app` chain 8453) — see `sandbox/pred-sandbox.yml`.

## Steps
1. **Login** — `loginWithSignature` (`POST /api/v1/auth/login-with-signature`) with header `X-API-Key` and an EIP-712 `CreateProxy` signature (domain `Pred Contract Proxy Factory`). Save `access_token`, `refresh_token`, `proxy_wallet_addr`, `user_id`, `is_enabled_trading`.
2. **Enable trading (only if `is_enabled_trading` is false/missing)** — `prepareSafeApproval` with `safe_wallet_address = proxy_wallet_addr`; sign the returned `transactionHash` with raw secp256k1 (no EIP-191 prefix); `executeSafeApproval` with `{ signature, data }`; then **call `loginWithSignature` again** (mandatory) to get a JWT with `is_enabled_trading=true`.
3. **Discover a market** — `getAllParentMarkets` (`GET /api/v1/market-discovery/discover?verbose=true&limit=50&offset=0`), paging `offset += limit` until `data.total` is exhausted. Use only rows where `parent_market_data.status == "active"` and the child `markets[].status == "active"`. Keep `parent_market_id`, `market_id`, and `parent_market_data.contract_address`.
4. **Read the orderbook** — `getOrderBook` (`GET /api/v1/order/{parentMarketID}/orderbook/{marketID}`); prices are in cents, sizes in shares.
5. **Place the order** — `placeOrder` (`POST /api/v1/order/{parentMarketID}/place`) with an EIP-712 `Order` signature (domain `Pred CTF Exchange` v1; `verifyingContract` = the parent's `contract_address`). Amount: Long = `(price*qty)/100`, Short = `((100-price)*qty)/100`. Send headers `Authorization: Bearer`, `X-Wallet-Address`, `X-Proxy-Address`.
6. **Confirm** — `getPositions` (`GET /api/v1/portfolio/positions`).

## Rules
- Auth model + headers: `authentication/pred-authentication.yml`.
- No HTTP idempotency key; order replay-safety is on-chain via the order `salt` + `nonce` (`conventions/pred-conventions.yml`).
- Error envelope and codes (e.g. `TRADING_NOT_ENABLED`, `REFRESH_TOKEN_ALREADY_USED`): `errors/pred-problem-types.yml`.
- Never hardcode the order contract — always take it from market discovery for the target parent market.
