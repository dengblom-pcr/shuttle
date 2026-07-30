# Shuttle Upgrade Tasks

## Phase 1 — Apple Silicon (minimal)
- [ ] Fix apple-scripts compile paths to be repo-relative
- [ ] Regenerate Shuttle/apple-scpt/*.scpt
- [ ] Restore or recreate missing icon assets (StatusIcon*.png, shuttle.icns)
- [ ] Set Release ARCHS=arm64 in Xcode project
- [ ] Build Release on Apple Silicon
- [ ] Verify `file` shows arm64 and app runs without Rosetta
- [ ] Smoke test Terminal + iTerm2 AppleScript handlers

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
