# Jirani — Neighborhood Delivery

A responsive React/TypeScript pilot for connecting customers with nearby foot and bicycle runners, with operations screens and server-side payment boundaries.

## Development

Requirements: Node.js 20+ and pnpm 10.18.0. Copy `.env.example` to `.env` and provide values through the project's protected configuration workflow. Never commit `.env` or service-account credentials. Firebase browser settings are public app configuration; Firebase Admin and Daraja values are server-only. This repository intentionally does not include Firebase setup instructions.

```sh
pnpm install
pnpm dev
```

The Express process serves the API and Vite development app on port 3000. `/api/health` reports service readiness. Missing provider configuration is shown as unavailable; the app does not invent accounts, order history, wallet balances, or completed payments.

## Build and deployment

```sh
pnpm check
pnpm build
PORT=3000 pnpm start
```

The production build writes the browser app to `dist/client` and the API to `dist/server`. Deploy the container with `PORT` supplied by the hosting platform and configure only server-side provider variables at runtime. Publish through the project's Webdev deployment flow after reviewing provider approval, privacy/security rules, and payment callback URLs. Publication is separate from building this repository. No live payment or production payout is enabled by default.

## Product boundaries

The delivery fees are KES 40 (0–300 m), KES 60 (300 m–1 km), and KES 90 (1–2 km), plus a KES 15 convenience fee; the runner receives 80% of the delivery fee and the platform 20%. These are product rules, not a claim that escrow or disbursements are active. At this foundation stage, order placement, wallet top-ups, and payments are disabled; `/api/orders` fails closed until verified runner matching, server-calculated distance quotes, and cancellation/settlement handling exist, and no balance is reserved. Daraja sandbox/production credentials, callback registration, authorized KYC handling, and applicable legal review are required before real transactions or identity evidence are handled.
