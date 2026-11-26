# `@pinkaphant/ecctrl` (`ecctrl`) — Agent & Contributor Guide

- **Active Release Baseline**: `@pinkaphant/ecctrl@2.0.4-beta.4` targets `"@dimforge/rapier3d-compat": "0.19.2"`, `"@react-three/rapier": "^2.2.0"`, `"@react-three/fiber": "^9.6.1"`, and `"three": "0.184.0"`.
- **Synchronous Rotor Stepping & Suspension Stability**:
  - `EcctrlVehicle` ([src/vehicles/EcctrlVehicle.tsx](./src/vehicles/EcctrlVehicle.tsx)) steps `wheel.current.step?.(state, delta)` and `propeller.current.step?.(state, delta)` synchronously inside its own `useFrame` right before reading `wheelsInfo` / `propellersInfo` and applying impulses, and preserves sleep state while idle (`return` on `body.isSleeping()`).
  - `ShapeCastWheel` ([src/vehicles/components/ShapeCastWheel.tsx](./src/vehicles/components/ShapeCastWheel.tsx)) computes relative hit velocity ahead of suspension force, clamps unilateral rebound (`Math.max(0, springForce - dampingForce)`), bounds damping and lateral impulses with semi-implicit effective point mass (`body.invMass()` + `body.effectiveWorldInvInertia()`), enforces lateral passivity sign clamping, and guards `gravityMag <= 1e-6` in zero-G worlds.
  - Pass `name="..."` on `<ShapeCastWheel>` and `<ThrustPropeller>` JSX elements.
- **Build & Verification**: Run `npm run build` (`vite build && tsc -p tsconfig.build.json`) and verify downstream `@khr3/core` (`npm test` in `../khr3`) before publishing via GitHub Actions OIDC (`.github/workflows/publish.yml`).
