# zennopay-docs

Mintlify source for [docs.zennopay.com](https://docs.zennopay.com) — the public
documentation for Zennopay QR Payments and Platform Payouts.

QR Payments embeds a native merchant-QR checkout in partner apps. Platform
Payouts is a server-to-server API for asynchronous bank payouts from a
prefunded balance.

## What lives here

| Section | Purpose |
|---|---|
| `introduction.mdx` | Product overview and routes into each integration |
| `qr-payments/` | Canonical QR Payments contract, availability, lifecycle, and errors |
| `quickstart.mdx` | QR Payments sandbox tutorial |
| `how-zennopay-works.mdx` | Product comparison and shared architecture |
| `payments/` | Accept payments: PaymentSheet overview, session endpoint, iOS, Android, Flutter, React Native, testing |
| `authentication.mdx` | HMAC-only partner auth + the Zennopay-minted session token, with test vectors |
| `concepts/` | QR funds flow and corridors, plus shared reconciliation guidance |
| `fundamentals/` | QR Payments per-user corridor limits |
| `platform-payouts/` | Platform Payouts overview, tutorial, field reference, webhooks, and sandbox tests |
| `api-reference/` | Shared conventions and QR Payment Intent endpoint reference |
| `changelog.mdx` | Release notes |

Old `/sdks/*` URLs redirect to `/payments/*` via the `redirects` array in
`docs.json`.

Each concept has one canonical owner: overview pages explain product choice,
quickstarts teach a happy path, API pages define fields and states, SDK pages
cover client integration, and `concepts/settlement.mdx` owns shared
reconciliation guidance.

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

- QR Payment debit examples use USD cents. Local-currency minor units and all
  Platform Payouts money fields use base-10 int64 strings; VND has no decimal
  places.
- Auth examples use placeholder secrets like `<your_secret>`. Never paste a
  real signing key into docs.
- Stubbed sections are marked with a "Coming soon" callout (🚧). When the
  underlying spec lands, fill the page and remove the callout in the same PR.
- Public docs must not include private commercial terms, provider-contract
  details, routing economics, customer/account data, or internal volumes.
