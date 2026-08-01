---
name: Stream PRED real-time order and market data
description: Obtain an Ably token from PRED and subscribe to real-time orderbook snapshots, last-traded price, and your own order events over WebSocket.
api: openapi/pred-openapi.yml
operations: [loginWithSignature, getAblyToken]
---

# Stream PRED real-time data

PRED delivers real-time data over [Ably](https://ably.com/) WebSocket. Use PRED's token endpoint as your Ably `authCallback`. See `asyncapi/pred-realtime-asyncapi.yml` for channel and message shapes.

## Steps
1. **Login** — `loginWithSignature` to obtain `access_token` and `user_id` (see the "Place a trade on PRED" skill).
2. **Get an Ably token** — `getAblyToken` (`POST /api/v1/auth/ably`) with `Authorization: Bearer <access_token>` (optionally `X-Wallet-Address`, `X-Proxy-Address`). The response is raw Ably `TokenDetails` JSON. Capabilities granted: `market:*` → subscribe; `private:user:<user_id>` → presence + subscribe.
3. **Connect to Ably** using that token as `authCallback`.
4. **Public market data** — subscribe to `market:{marketId}` for `WSOrderBookSnapshot` (bids/asks) and `WSLastTradedPrice`.
5. **Your order events** — for `private:user:{userId}` you MUST **enter Ably Presence first** (e.g. `channel.Presence.Enter`), otherwise PRED delivers no events. Then subscribe to `order-created`, `order-updated`, and `order-cancelled`.

## Rules
- You can only subscribe to your own `user_id` channel.
- Presence entry is mandatory on the private channel before events flow.
- Token/auth details: `authentication/pred-authentication.yml`.
