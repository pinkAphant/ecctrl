# `@pinkaphant/ecctrl` (`ecctrl`) — Agent & Contributor Guide

- **Canonical Source Contract (`ad6ee7f`)**: `src/` is pure upstream `pmndrs/ecctrl@2.0.2` (`e2cab80`) plus the single 1-line `return` after `body.wakeUp()` in [src/vehicles/EcctrlVehicle.tsx](./src/vehicles/EcctrlVehicle.tsx) so sleeping vehicles skip wheel impulses on the wake frame when gravity was skipped. Keep `src/` byte-for-byte identical to `ad6ee7f`.
- **Target Runtime Stack**: `"@dimforge/rapier3d-compat": "0.19.2"`, `"@react-three/rapier": "^2.2.0"`, `"@react-three/fiber": "^9.6.1"`, and `"three": "0.184.0"`.
- **Build & OIDC Publishing**: Run `npm run typecheck && npm run build` (`vite build && tsc`) and publish via GitHub Actions OIDC Trusted Publishing ([.github/workflows/publish.yml](./.github/workflows/publish.yml)).
