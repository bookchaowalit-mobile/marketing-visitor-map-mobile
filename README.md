# Visitor Map — Mobile

## Template copy

This repo is one of the name-substituted Expo SDK 53 / Expo Router template
copies in the `bookchaowalit-mobile` org. The canonical template is
[`bookchaowalit-mobile/community-hub-mobile`](https://github.com/bookchaowalit-mobile/community-hub-mobile).
Consolidating or archiving this copy is pending owner decision D5 (BD-033); see
`repository-catalog/portfolio/MOBILE-CONSOLIDATION-2026-10.md` in solo-empire.
This copy keeps its own code and its own copy of the CI workflow (no shared package).

React Native mobile app (Expo) for **Visitor Map**.

Part of [Chaowalit Greepoke](https://bookchaowalit.com)'s 101 Portfolio Projects.

## Features

- **Visitor map** (Map tab): plots visits on an equirectangular world grid, with
  nearby visits clustered into dots sized by volume, a 24h / 7d / 30d / all range
  filter, and a top-countries table with flags, counts and share bars. It uses
  deterministic sample data until the analytics backend is connected.
- Aggregation, clustering and projection live in `lib/visitors.ts` (pure
  TypeScript, unit-tested).

## Tech Stack

- **Framework:** Expo SDK 53 + Expo Router
- **Language:** TypeScript
- **Navigation:** Expo Router (file-based)
- **UI:** React Native + Ionicons

## Getting Started

```bash
npm install
npx expo start
```

## Scripts

```bash
npm run typecheck   # tsc --noEmit
npm run lint        # expo lint (eslint-config-expo)
npm test            # vitest unit tests for lib/
npx expo export --platform android --output-dir dist   # JS bundle smoke check
```

CI (`.github/workflows/ci.yml`) calls the shared
`bookchaowalit/platform-ci-workflows` v1.1.1 (pinned by SHA): `npm ci`, lint,
typecheck, `vitest run`, then the Android JS bundle export, plus the security
scans (gitleaks, Semgrep, OSV-Scanner, Trivy). Nothing is masked. Reviewed
scanner exceptions, each with a reason and expiry, are in `osv-scanner.toml`
and `.trivyignore`. EAS / Expo cloud builds are not run in CI: they need the
owner's Expo account (`EXPO_TOKEN`), so they stay a manual owner step.

## Build

```bash
# Android
npx eas build --platform android --profile preview

# iOS
npx eas build --platform ios --profile preview
```

## Related

- **Frontend:** [bookchaowalit-website/visitor-map-frontend](https://github.com/bookchaowalit-website/visitor-map-frontend)
- **Portfolio:** [bookchaowalit.com](https://bookchaowalit.com)

## License

MIT
