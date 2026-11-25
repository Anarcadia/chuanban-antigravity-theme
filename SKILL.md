---
name: chuanban-antigravity-theme
description: Warm-paper editorial theme, Claude-inspired typography, compact context menus, live context metrics capsule, and local SQLite Token Analytics for Google Antigravity 2.0 (v6.0.4 Global English Lightweight Edition · compatible with Antigravity 2.35.2+ / 2.35.0 / 2.34.0+ on macOS, Windows, and Linux). Zero `.asar` tampering, zero npm dependencies, <1 MB font download (or 0 MB pure native mode), 5-preset appearance switcher with Follow System pairing, and 2.5s hot-reload user layer. Trigger when the user asks to install, upgrade, customize, or troubleshoot the Chuanban Antigravity Theme.
---

# Chuanban Antigravity Theme (v6.0.4 · Global Lightweight Edition — AI Agent Deployment Contract)

## 0. Mandatory AI Agent Onboarding & Adaptive Language Protocol

1. **Match the User's Conversation Language Immediately**:
   - Always reply in the **same language the user used in their prompt** (English, Japanese, Korean, German, Spanish, French, etc.).
   - If the user only pasted a repository path/URL with no clear language cue, inspect `edition.systemLocale` from `node install.mjs doctor` in Step 1 and greet/guide them in their OS language.
2. **Parallel Edition Routing (Zero Cross-Contamination)**:
   - **This repository (`chuanban-antigravity-theme`) is the Global Pure-English UI Lightweight Edition**: it physically omits all CJK translation dictionaries and the 170–791 MB Sarasa Gothic font requirement (`< 1 MB` Anthropic Serif/Mono download, or `0 MB` with `--font-mode native`). It keeps Antigravity's UI 100% in crisp English while providing the full warm-paper palette, typography, context menus, live metrics pill, and Token Analytics.
   - **If `edition.chineseUiHint` is non-null OR the user explicitly asks in Chinese for UI localization (`汉化`)**: inform them concisely in Chinese that this is the pure-English lightweight edition, and offer to either proceed with this lightweight English-UI theme or use the parallel Simplified Chinese edition (`https://github.com/Anarcadia/chuanban-antigravity-theme-patch`).

---

## 1. Architecture & Core Capabilities

- **Non-Invasive Loopback CDP Runtime Injection**: Never modifies `app.asar`, never breaks macOS/Windows code signing, requires zero third-party `npm` packages.
- **Five-Preset Appearance Bar & Follow System**:
  - Default **`"morandi"`** (Warm Xuan-paper canvas × Slate-Mineral single `2px` composer border);
  - Embedded in **Settings → Appearance**: **`[ A Original | ✳️ Absolutely! | MO Morandi | 📖 Warm Dark | 🌙 Dark ]`** + **`Follow System`** automatic light/dark pairing toggle, synced seamlessly with Windows `TitleBarOverlay` (`--custom-window-controls`) and Swarm subframes.
- **Two Ultra-Light Font Modes (`< 1 MB` or `0 MB`)**:
  - **`--font-mode anthropic` (Default, `< 1 MB` total)**: UI controls use Antigravity's native variable `Google Sans Flex`; chat prose uses `Anthropic Serif`; code, inline file pills, and composer use `Anthropic Mono`. Automatically fetched from Cloudflare R2 / GitHub Release mirrors with SHA-256 verification.
  - **`--font-mode native` (`0 MB` instant install)**: Zero font downloads — uses native `Google Sans Flex` and system monospace throughout.
- **Claude-Style Compact Context Menus & Safe IDE Bridge**:
  - Theme-matched context menu cards for file pills (`Open in Editor`, auto-detected installed external IDEs like VS Code / Cursor / Zed / JetBrains / Sublime, `Reveal in Finder / Explorer`, `Copy Path`), web links, code blocks, chat images, and the bottom composer (`Shift + Right-Click` always passes through to the native OS menu).
- **Live Context Metrics Capsule & Local Token Analytics**:
  - Read-only `node:sqlite` telemetry pill below the composer (`260ms` hover intent, auto-hidden on Remote SSH when no local `.db` exists) + **Settings → Local Extensions → Token Analytics** multi-dimensional attribution dashboard.
- **Two Strict Guardrails for Agents**:
  1. **Never hand-edit `core/`**: `core/*` is protected by `core/manifest.json` SHA-256 integrity checks. Always deploy via `node install.mjs`.
  2. **Customize exclusively inside `~/.gemini/antigravity/theme-patch/user/`**: `user/` is never overwritten during upgrades and hot-reloads within `2.5s`.

---

## 2. Node.js Runtime Tiers

> Prefer **Node.js `>= 22.13.0`** when multiple Node versions (`nvm` / `fnm` / `volta` / Homebrew) are present (`install.mjs` pins `process.execPath` into the OS autostart service).

| Node.js Version | 5-Preset Theme + Follow System / Fonts / Context Menu | Deadlock & Cold-Boot Healer + M2 Relay | Live SQLite Metrics Pill + Token Analytics (`node:sqlite`) |
| :--- | :---: | :---: | :---: |
| **Node.js `>= 22.13.0`** (Recommended) | ✅ Enabled | ✅ Enabled | ✅ **Enabled** |
| **Node.js `22.0.0 ~ 22.12.x`** | ✅ Enabled | ✅ Enabled | ⚠️ Gracefully disabled (zero errors) |
| **Node.js `< 22.0.0`** | ❌ Blocked by `install.mjs` | — | — |

---

## 3. Standard 3-Step AI Agent Deployment Flow

### Step 1: Pre-flight Environment & Font Check
```bash
node install.mjs doctor
```
Inspect `edition.systemLocale`, `fonts.allRequiredInstalled`, `fonts.missing`, and `fonts.unregisteredWarning`:
- **If `fonts.allRequiredInstalled === false`** (and the user wants the default `anthropic` serif/mono typography):
  ```bash
  # Auto-downloads the 3 lightweight Anthropic*.ttf files (< 1 MB total) via Cloudflare R2 -> GitHub Release -> Google Drive failover and registers them (UTF-16 HKCU registry + WM_FONTCHANGE on Windows)
  node install.mjs install-fonts --auto-download
  ```
  - If the user prefers **zero font downloads (`0 MB`)**, skip `install-fonts` and pass `--font-mode native` in Step 2.
  - On Windows, if `install-fonts` returns `restartAntigravityRequired: true`, restart Antigravity once after Step 2 so DirectWrite picks up newly registered fonts.

### Step 2: Install Core & Register Autostart Service
```bash
# Default install (preset="morandi", fontMode="anthropic", channel="auto" covering both Stable & Insiders)
node install.mjs install

# Zero-font-download pure native typography mode:
node install.mjs install --font-mode native

# Optional initial preset selection:
node install.mjs install --preset absolutely --dark-preset claude-warm
```
**Critical Edge-Case Handling**:
1. **Single-Icon Clean Mode**:
   - Windows patches existing `Antigravity.lnk` shortcuts in place with `--remote-debugging-port=0` while preserving proxy settings; Linux writes `~/.local/share/applications/antigravity.desktop`;
   - **macOS (`"launcherMode": "single-icon-m2-relay"`, `"launcherInstalled": false`) is expected by design** — no duplicate `.app` icon is created unless `--with-launcher` is passed.
2. **Preventing Self-Termination When Running Inside Antigravity**:
   - If `install` or `doctor` reports `"cdpStatus": "missing_opt_in_flag"`:
     - **If you (the Agent) are running inside Antigravity's own chat**: **NEVER run `relaunch --force`!** Simply tell the user installation is complete and ask them to quit and reopen Antigravity once after your reply finishes (the background daemon's M2 relay will seamlessly attach), or run `node ~/.gemini/antigravity/theme-patch/install.mjs relaunch` from an external terminal.
     - **If you are running from an external terminal** (Claude Code, Codex, iTerm2, Windows Terminal) and Antigravity is idle: run `node install.mjs relaunch`.

### Step 3: Live CDP Injection Verification
```bash
node install.mjs verify
```
When `"ok": true`, `"bodyReady": true`, and `"hasStyle": true` are returned, the theme, typography, context menus, and live telemetry capsule are active in the live window.

---

## 4. Hot-Reload Customization (`~/.gemini/antigravity/theme-patch/user/`)

Edits inside `user/` take effect automatically within `2.5s` without restarting the daemon or Antigravity:

- **`user/config.json`**:
  - `"preset"`: `"morandi"` | `"absolutely"` | `"native"` | `"claude-desktop-purewhite"` | `"vintage-deep"`
  - `"darkPreset"`: `"onyx"` | `"claude-warm"`
  - `"fontMode"`: `"anthropic"` | `"native"` (hot-swappable in `2.5s`!)
  - `"modules"`: toggle `"metrics"`, `"tokenAnalytics"`, `"composerWaxSeal"`, `"contextMenu"`, `"cdpAutoRelaunch"`, `"customCss"`, `"customJs"`, or set top-level `"enabled": false` to cleanly unload all styles live.
  - `"themeVars"` / `"darkThemeVars"`: e.g. `{ "--ag-chat-font-size": "16px" }`.
- **`user/custom.css`**: Append standard CSS (`#antigravity-user-custom-style`).
- **`user/custom.js`**: Sandboxed frontend hook with `ctx.onCleanup(fn)`.

### Troubleshooting & Rollback
```bash
node install.mjs verify --safe-mode   # Bypass user/ layer to isolate custom CSS/JS issues
node install.mjs rollback             # Restore previous core/ backup snapshot immediately
node install.mjs uninstall            # Stop daemon, remove autostart & unload live styles (keeps user/)
```
