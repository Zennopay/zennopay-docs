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
| `payments/` | Accept payments: PaymentSheet overview, session endpoint, iOS, Android, Flutter, React Native, testing |
| `authentication.mdx` | HMAC-only partner auth + the Zennopay-minted session token, with test vectors |
| `concepts/` | QR funds flow and corridors, plus shared reconciliation guidance |
| `fundamentals/` | QR Payments per-user corridor limits |
| `platform-payouts/` | Platform Payouts overview, USD deposits and conversion, tutorial, field reference, webhooks, and sandbox tests |
| `api-reference/` | Shared conventions and downloadable QR Payments and Platform Payouts OpenAPI reference |
| `changelog.mdx` | Release notes |

The retired `/how-zennopay-works` page redirects to the introduction.
Old `/sdks/*` URLs redirect to `/payments/*` via the `redirects` array in
`docs.json`.

Each concept has one canonical owner: overview pages explain each product and its integration steps,
quickstarts teach a happy path, API pages define fields and states, SDK pages
cover client integration, and `concepts/settlement.mdx` owns shared
reconciliation guidance.

## Preview locally

```bash
npx mintlify dev
```

The site renders at [http://localhost:3000](http://localhost:3000). Mintlify
hot-reloads on file save.

## Validate changes

```bash
npx mintlify validate
npx mintlify broken-links
```

Cross-check API behavior against `Zennopay/zennopay-mono-mvp` and SDK examples
against the relevant SDK release. Funding routes are documented in
`platform-payouts/funding.mdx`; they are not yet included in `openapi.json`.

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

## Page formatting

The docs use Mintlify Maple with a persistent sidebar, Inter Tight headings, and
Zennopay accents. `style.css` styles the welcome page, product artwork, and code typography.

- Welcome: introduction and quick links, illustrated products, guide cards, then reference links.
- Guides: state the outcome, prerequisites, numbered steps, then next actions.
- Product overviews: explain the product before linking to related guides.
- API references: keep field tables, code samples, statuses, and errors.
- Use short sidebar titles and preserve existing routes when reorganizing.

The layout was adapted from https://docs.treasury.sh/ at the user's request.

Product artwork in `images/products/` is reused unchanged from the Zennopay landing page (`public/illustrations/`). Keep the 480px and 960px WebP variants together when updating these assets.

Typography follows the landing page: **Inter Tight** for headings, **Inter** for body text, and **JetBrains Mono** for code. Heading and body fonts are configured in `docs.json`; the code font is loaded in `style.css`.

Buttons reuse the landing page’s pill shape and theme-aware iris/lavender gradients. Liquid glass is limited to the welcome quickstart panel, product cards, and overview artwork panels; guide cards use quieter tinted surfaces. CSS includes reduced-motion support and an opaque fallback for browsers without backdrop blur.
