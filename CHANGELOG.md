# Changelog

Notable changes to Ecctrl are documented here.

## 2.0.4-beta.4 - 2026-11-26

- Fixed vehicle wake-up bump by returning after `body.wakeUp()` on frames where gravity was skipped while asleep (`EcctrlVehicle`).
- Eliminated 2-frame suspension/tire impulse lag by stepping registered `ShapeCastWheel` and `ThrustPropeller` instances synchronously inside `EcctrlVehicle` before applying impulses, and computing `rayHitPointVelocity` before suspension damping (`ShapeCastWheel`).
- Clamped unilateral suspension support impulse (`Math.max(0, springForce - dampingForce)`) so tires never pull the chassis downward during rebound (`ShapeCastWheel`).

## 2.0.2 - 2026-09-06

- Fixed a bug where ground information only refreshed after releasing and pressing a movement key again.

## 2.0.1 - 2026-08-16

- Improved joystick tracking and removed drag jitter on lower-frame-rate touch devices.
- Added reliable pointer capture, cancellation, and multi-touch handling to the joystick and virtual buttons.
- Reduced touch-control renders, layout reads, and redundant store updates.
