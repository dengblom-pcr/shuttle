# Shuttle Upgrade Tasks

## Phase 1 — Apple Silicon (minimal)
- [x] Fix apple-scripts compile paths to be repo-relative
- [x] Regenerate Shuttle/apple-scpt/*.scpt (Terminal + Virtual; iTerm needs iTerm2 installed — committed .scpt kept)
- [x] Restore or recreate missing icon assets (StatusIcon*.png, shuttle.icns)
- [x] Set Release ARCHS=arm64 in Xcode project
- [x] Build Release on Apple Silicon (`build/Release/Shuttle.app` — **BUILD SUCCEEDED**)
- [x] Verify `file` shows arm64 and app runs without Rosetta (`Mach-O 64-bit executable arm64`)
- [x] Smoke test Terminal + iTerm2 AppleScript handlers (Terminal handler OK — new window ran `echo SHUTTLE_PHASE1_SMOKE_OK`; Automation already granted for `shuttle.Shuttle`; iTerm2 not installed so iTerm handlers skipped)
- [x] License / attribution for personal GitHub fork (keep open source, free; no logo changes)
  - [x] Keep MIT `LICENSE` with original `Copyright (c) 2013 Trevor Fitzgerald` notice
  - [x] Add your copyright line for modifications (`Copyright (c) 2026 David Engblom`)
  - [x] Update `NSHumanReadableCopyright` in `Shuttle/Shuttle-Info.plist` (About box reads this) — credit fork maintainer + note based on original
  - [x] Update README for your GitHub remote (install/build links, retain credit to Trevor Fitzgerald / original project)
  - [x] Leave logo / icons unchanged (`shuttle.icns`, `StatusIcon*.png`)

## Phase 2 — Build & project hygiene
- [ ] Add Shuttle.xcodeproj/xcshareddata/xcschemes/Shuttle.xcscheme for CLI builds
- [ ] Bump MACOSX_DEPLOYMENT_TARGET (10.8/10.9 → 11.0+; Apple Silicon Macs require Big Sur minimum anyway)
- [ ] Upgrade project format (objectVersion 46 / LastUpgradeCheck 1010 → current Xcode)
- [ ] Commit generated .scpt and icons OR add a "prepare" build script + document in README
- [ ] Add basic build instructions to README (replace prebuilt-only install flow)

## Phase 3 — Code signing & distribution
- [ ] Set DEVELOPMENT_TEAM and CODE_SIGN_IDENTITY (currently empty)
- [ ] Enable Hardened Runtime (ENABLE_HARDENED_RUNTIME = YES)
- [ ] Review entitlements: replace temporary Apple Events exception with proper Automation usage
- [ ] Notarize for Gatekeeper-friendly distribution
- [ ] Publish arm64 (or universal) release replacing fitztrev.github.io Intel binary

## Phase 4 — Deprecated API modernization
- [ ] Replace LSSharedFileList login-item APIs in LaunchAtLoginController.m with SMAppService (macOS 13+) or ServiceManagement
- [ ] Convert LaunchAtLoginController.m to ARC (currently -fno-objc-arc)
- [ ] Remove NSMakeCollectable usage (deprecated)
- [ ] Audit manual retain/release in AppDelegate.m for ARC migration

## Phase 5 — AppleScript & terminal compatibility
- [ ] Test all 9 AppleScript handlers against current Terminal.app and iTerm2
- [ ] Verify iTerm2 bundle ID in Shuttle.entitlements (com.googlecode.iterm2)
- [ ] Update iTerm nightly scripts if iTerm API changed since 2016
- [ ] Consider consolidating iTerm stable/nightly script variants

## Phase 6 — CI & quality
- [ ] Add GitHub Actions: xcodebuild on macos-latest (arm64 runner)
- [ ] Add lint/static analysis pass
- [ ] Document test configs in tests/ for regression checks

## Phase 7 — Nice-to-have (from CHANGELOG roadmap)
- [ ] Preferences panel
- [ ] Update notifications
- [ ] Keyboard hotkeys
- [ ] Cloud provider menu integration
