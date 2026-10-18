# Digital Energy Solana RPC for AI agents (x402 + MPP)

**Endpoint:** https://agents.digital-energy.io/
**Price:** 0.005 USDC per HTTP request, paid on Solana mainnet. No signup, no API key.
**Protocols:** x402 (v2, exact) and MPP. Every unpaid request gets an HTTP 402 offering both.
**Batches:** up to 15 JSON-RPC calls per request, settled as one payment.

## Try it
Unpaid request (returns the 402 payment challenge):

    curl -i -X POST -H 'content-type: application/json' \
      -d '{"jsonrpc":"2.0","id":1,"method":"getSlot"}' https://agents.digital-energy.io/

Paid request with the pay CLI (https://solana.com/docs/payments/pay-sh):

    pay --x402 fetch -X POST --content-type application/json \
      --body '{"jsonrpc":"2.0","id":1,"method":"getSlot"}' https://agents.digital-energy.io/

## Not available on this endpoint
- getProgramAccounts, getSupply, getLargestAccounts, getTokenLargestAccounts (return -32601)
- Batches of 16 or more calls, request bodies over 30 KB
- WebSocket subscriptions (HTTP JSON-RPC only)

Transaction history covers about the last 15 hours.

## Operator
Digital Energy, a Solana validator operator, serving from its own hardware.
Keyed plans with full method access and WebSockets: https://rpc.digital-energy.io
Service status: https://status.digital-energy.io
