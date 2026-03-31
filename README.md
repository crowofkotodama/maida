# Maida

If Maida helps you, buy me a coffee:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/W7W21WT2FT)

Maida is a cross-platform desktop app built with **Tauri 2 + React + Vite**.

It helps Steam players cut through library paralysis by replacing endless browsing with a simpler interaction: show one installed game, decide **Try it now** or **Not now**, then move on.

This repository is the application source for the Maida desktop client, not a landing page or manifesto. The README below is written accordingly.

## App Summary

- **Product name:** Maida
- **Current version:** `0.1.0`
- **App identifier:** `com.brightraven.maida`
- **Frontend:** React 18 + Vite 7
- **Desktop runtime:** Tauri 2
- **Backend language:** Rust 2021
- **Package manager:** pnpm `10.28.2`
- **Supported UI languages:** English, Japanese, Simplified Chinese, Traditional Chinese
- **Target platforms:** Windows, Linux
- **Release bundle targets:** NSIS, `.deb`, AppImage

## What the App Does

Maida is designed for the moment when a player has plenty of installed games but cannot cleanly start one.

Core flow:
1. Read the local installed-game set from Steam.
2. Present one candidate at a time.
3. Let the player decide: **Try it now** or **Not now**.
4. Preserve momentum instead of turning leisure into another optimization problem.

Maida is intentionally **not**:
- a recommendation engine
- a backlog manager
- a social feed
- a retention loop
- a guilt machine for unfinished games

## Current Feature Surface

### Core product flow
- Steam installed-game detection
- Single-game presentation flow
- Session logic for accept / skip decisions
- Persistent local state
- Onboarding flow for first use

### Interaction and interface
- Full keyboard navigation
- Gamepad support
- Screen-reader-aware desktop UI
- Error boundary and recovery handling
- Theme handling and desktop-style application shell

### Content and localization
- English (`en`)
- Japanese (`ja`)
- Simplified Chinese (`zh-CN`)
- Traditional Chinese (`zh-TW`)

### Desktop integration
- Tauri IPC bridge between frontend and Rust backend
- Native updater integration
- Single-instance handling
- Native dialog / opener / store plugins

## Tech Stack

### Frontend
| Dependency | Version |
|---|---:|
| react | `^18.2.0` |
| react-dom | `^18.2.0` |
| vite | `^7.3.0` |
| @vitejs/plugin-react | `^4.2.1` |

### Tauri / desktop
| Dependency | Version |
|---|---:|
| @tauri-apps/api | `^2.10.1` |
| @tauri-apps/cli | `^2.10.1` |
| @tauri-apps/plugin-process | `~2.3.1` |
| @tauri-apps/plugin-updater | `~2.10.0` |
| tauri | `2` |
| tauri-build | `2` |
| tauri-plugin-dialog | `~2` |
| tauri-plugin-opener | `~2` |
| tauri-plugin-single-instance | `~2` |
| tauri-plugin-store | `~2` |
| tauri-plugin-updater | `~2` |

### Rust backend
| Crate | Version |
|---|---:|
| serde | `1` |
| serde_json | `1` |
| reqwest | `0.12` |
| tokio | `1` |
| keyring | `3` |
| regex | `1` |
| chrono | `0.4` |
| log | `0.4` |
| uuid | `1` |
| rand | `0.9` |
| winreg *(Windows only)* | `0.55` |
| tempfile *(dev)* | `3` |

### Testing and QA
| Dependency | Version |
|---|---:|
| vitest | `^4.0.18` |
| @vitest/coverage-v8 | `^4.0.18` |
| @playwright/test | `^1.58.2` |
| @axe-core/playwright | `^4.11.1` |

## Repository Structure

```text
.
├── src/                  # React frontend
├── src-tauri/            # Rust backend + Tauri config
├── e2e/                  # Playwright accessibility / e2e tests
├── .github/workflows/    # CI and release automation
├── package.json          # JS scripts and dependency versions
├── pnpm-lock.yaml        # Locked JS dependency graph
└── README.md
```

More detailed frontend architecture notes live in `src/README.md`.

## Development Requirements

### Required tools
- **Node.js** compatible with the current pnpm / Vite / Tauri toolchain
- **pnpm `10.28.2`**
- **Rust stable toolchain**
- **Tauri build prerequisites** for your platform

### Linux packaging/runtime dependencies
The current Linux bundle config declares:
- `libwebkit2gtk-4.1-0`
- `libgtk-3-0`

The current GitHub release workflow installs these build dependencies on Ubuntu:
- `libwebkit2gtk-4.1-dev`
- `libappindicator3-dev`
- `librsvg2-dev`
- `patchelf`

## Install Dependencies

```bash
pnpm install
```

## Run in Development

```bash
pnpm run tauri:dev
```

This starts the Vite dev server and launches the Tauri desktop shell against `http://localhost:5173`.

## Build the App

```bash
pnpm run tauri:build
```

Current Tauri bundle targets:
- `nsis`
- `deb`
- `appimage`

## Frontend-only Commands

```bash
pnpm run dev
pnpm run build
pnpm run preview
pnpm run lint
```

## Test Commands

```bash
pnpm run test
pnpm run test:watch
pnpm run test:coverage
pnpm run test:e2e
```

## CI / Release Automation

### Test workflow
GitHub Actions currently runs:
- unit tests on `push` to `main`
- unit tests on pull requests to `main`
- Playwright accessibility / e2e coverage on pull requests to `main`

CI currently uses:
- **Node.js 24**
- **pnpm**
- Ubuntu runners for tests

### Release workflow
Tagged releases (`v*`) currently build on:
- `windows-latest`
- `ubuntu-22.04`

The release pipeline:
- installs Rust stable
- restores Rust cache
- installs platform dependencies
- runs tests
- builds the Tauri application
- drafts a GitHub release with updater metadata

## Configuration Notes

### App window
Current desktop window configuration:
- initial size: `1200 × 800`
- minimum size: `1024 × 680`
- resizable: yes

### Updater
The updater is configured to read release metadata from:
- `https://github.com/devBrightRaven/maida/releases/latest/download/latest.json`

### Content Security Policy
The current Tauri CSP allows outbound connections for app functionality to:
- `https://api.igdb.com`
- `https://id.twitch.tv`
- Steam and IGDB image CDNs

## Accessibility

Current repository signals for accessibility work include:
- keyboard-first interaction support
- screen reader support targets
- Playwright + axe-based accessibility testing
- localization across four UI languages

## Privacy

Maida is designed around local use.

Current behavior documented in the product copy:
- game data stays on device
- one anonymous launch ping may be sent with a random ID and install day count
- telemetry can be turned off in Settings

If this behavior changes, the README should be updated alongside the app and privacy-facing screens.

## Status

Current repository state suggests:
- active desktop app development
- Tauri 2 migration already in place
- automated test and release workflows configured
- Windows and Linux as the primary shipping targets

## License

Copyright 2026 Bright Raven World. All rights reserved.
