# zennopay-docs

Mintlify source for [docs.zennopay.com](https://docs.zennopay.com) — the public
documentation for the Zennopay cross-border QR payments API.

Zennopay is a B2B fintech API that lets partner fintechs embed cross-border
QR payments for their users — pay at a Thai PromptPay or Vietnamese VietQR
merchant from a USD wallet balance.

## What lives here

| Section | Purpose |
|---|---|
| `introduction.mdx` | One-page overview of what Zennopay does and who uses it |
| `quickstart.mdx` | 10-minute onboarding for partner backends |
| `authentication.mdx` | HMAC + JWT dual-layer auth, with test vectors |
| `api-reference/` | REST endpoints (Payment Intents, Webhooks) |
| `sdks/` | The PaymentSheet: overview, iOS, Android, Flutter, React Native, session endpoint |
| `concepts/` | Funds flow, corridors, settlement & reconciliation |
| `changelog.mdx` | Release notes |

## Preview locally

```bash
npm i -g mintlify
mintlify dev
```

The site renders at [http://localhost:3000](http://localhost:3000). Mintlify
hot-reloads on file save.

## Deploy

Pushes to `main` deploy automatically via the Mintlify GitHub integration.
Contact the docs maintainers if the integration needs reconnecting.

## Conventions

- All money examples use USD. Local-currency math belongs in the corridor /
  funds-flow pages, not in API examples.
- Auth examples use placeholder secrets like `<your_secret>`. Never paste a
  real signing key into docs.
- Stubbed sections are marked with a "Coming soon" callout (🚧). When the
  underlying spec lands, fill the page and remove the callout in the same PR.
