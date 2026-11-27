# Changelog

Notable changes to Ecctrl are documented here.

## 2.0.4-beta.5 - 2026-11-26

- Restored canonical `ad6ee7f` (`pmndrs/ecctrl@2.0.2` + 1-line `return` after `body.wakeUp()` in `EcctrlVehicle` so sleeping vehicles skip wheel impulses on the wake frame when gravity was skipped).

## 2.0.2 - 2026-09-06

- Fixed a bug where ground information only refreshed after releasing and pressing a movement key again.

## 2.0.1 - 2026-08-16

- Improved joystick tracking and removed drag jitter on lower-frame-rate touch devices.
- Added reliable pointer capture, cancellation, and multi-touch handling to the joystick and virtual buttons.
- Reduced touch-control renders, layout reads, and redundant store updates.
