# Changelog

## [v6.1.0] - 2026-11-28 — Meadow Inkstone (`meadow`) & Forest Night (`forest-night`) Botanical Skins + 7-Slot Switcher

- **Added Two Independent Modern Flat Botanical Skins (`meadow` & `forest-night`) and Upgraded Appearance Bar to 7 Slots (`core/theme.css` / `core/runtime.js` / `core/daemon.mjs` / `install.mjs`)**:
  - **🌱 Meadow Inkstone (`meadow` · Light)**: Imperceptible isotropic `256×256` lossless opaque WebP micro-limestone canvas (`#FAFBF9`) paired with an inkstone outer shell/sidebar (`#E9EDE9`), forest-green primary accents (`#386B4B` / `#80C776`), `1px` flat composer, and all-green live metrics hover cards (preserving critical red alerts at `>= 90%`).
  - **🌲 Forest Night (`forest-night` · Dark)**: Warm pine-charcoal canvas (`#181B18`) with moss-slate cards (`#202420`), 100% opaque `backdrop-filter: none` menus, and decoupled `Follow System` cross-pairing (`'Default Dark'` host `localStorage` masking).
  - **Platform-Calibrated Sans-Serif Prose**: Switches chat prose to `Google Sans Flex` (`wdth: 100`, `slnt: -10` italics) while preserving `Anthropic Mono` code blocks; enables subtle ink-bleed on macOS (`darwin`) while enforcing 100% zero ink-bleed (`text-shadow: none !important`) and crisp `600` bold weights on Windows (`win32`) DirectWrite.

## v6.0.6 (2026-11-28) — Two-Stage Transactional Hot-Upgrade Engine & Antigravity `2.36.0` Adaptation

- **Added Dual-Mirror Read-Only Update Check & In-Place Transactional Hot-Upgrade (`install.mjs` / `core/daemon.mjs` / `core/runtime.js` / `core/theme.css`)**:
  - Added lightweight `core-update-v6.0.6.zip` (~269 KB) & `latest.json` dual-mirror probing (`Cloudflare R2` + `GitHub Releases`, dual SHA-256 verification, symlink/NTFS Junction guards, once-per-24h background check with `modules.updateCheck: false` opt-out) and one-click **Update Now** in **Settings → Appearance**.
  - Implemented 3-phase `upgrade.lock` (`download → commit → service_handoff`), multi-window live version advance verification, automatic rollback on failure without restarting the Antigravity client, and NTFS `EPERM/EBUSY` atomic rename retries.
- **Full Antigravity `2.36.0` (`CL=1031268331`) UI & Performance Alignment (`core/theme.css` / `core/runtime.js` / `core/daemon.mjs`)**:
  - Adapted maximized auxiliary-pane `.agy-floating-composer-pill` concentric radius (`22px` collapsed / `18px` expanded) and split-pane `resolveBoxCascadeId` UUID lookup; fixed Tailwind v4 `@layer utilities` `!bg-background/70` cascade inversion on boxed `[data-testid="agent-message-bubble"]` inline/block code via `@layer base` overrides (`--ag-bubble-*` escape hatches); fixed Settings search × Token Analytics tab navigation; ported virtualized Diff `.code-line` / `.view-lines` observer fast-skip and `[data-ag-plugin-ui]` / `[data-ag-sb-ui]` / `[data-ag-quota-ui]` `user/` add-on fast-skip.

## v6.0.5 (2026-11-26) — WSL2 Token Analytics Deadlock Fix & Native Preset State Machine Closure

- **Resolved Windows + WSL2 400ms UNC Backoff Deadlocks Across Live Lineage & Token Analytics (`core/daemon.mjs` / `core/runtime.js`, PR #49)**:
  - Decoupled cooperative multi-file slicing (`refreshLineageIndex` cursor slices + Token Analytics local deadlines `stat <= 4s`, `parse <= 6s` sorted by `conversation_summaries.db` recency) from single-call 9P stall circuit-breakers, eliminating cascading 45s `wslUncBackoffUntil` blackouts on WSL2 workspaces with `>160` conversation DBs.
  - Added preemptible, livelock-free background micro-batch warmup (`runTokenAnalyticsBgWarmup` + `tokenAnalyticsFgAbortSeq`, `newlyCachedCount > 0` progress gate, zero-`statSync` cache skip, `bypassStagingLru` + active-WAL-only 6-slot staging isolation with per-entry 10m idle eviction, unified `dbCount` denominator, and automatic `4s` silent panel convergence while `warming…`).
- **Fixed Dark-to-Original (`A`) Preset Switching & Follow System Closure (`core/runtime.js`, Issue #48)**:
  - Clicking `A` (`Original Theme`) from dark mode while `Follow System` is off now triggers an internal native `light` click to exit `body.dark`, while keeping `Original Light · Original Dark` auto-switching intact when `Follow System` is enabled.
- **Claude & GPT Quota Pool Alignment (`core/daemon.mjs` / `core/runtime.js`)**:
  - Updated `thinkUnreported` detection to include `gpt-*` (`apiProvider` 31/32) alongside Claude models.

## v6.0.4 (2026-11-26) — Initial Global Lightweight Parallel Release

- **Decoupled Pure-English Lightweight Architecture**:
  - Physically stripped the ~68 KB CJK DOM `MutationObserver` translation engine, Swarm polling translation shields, and all CJK dictionaries (`core/runtime.js` reduced by ~98 KB).
  - Removed the 170–791 MB Sarasa Gothic CJK font requirement: defaults to `< 1 MB` `Anthropic Serif` + `Anthropic Mono` auto-download (Cloudflare R2 → GitHub Release → Google Drive failover), plus a zero-download `--font-mode native` (`0 MB`) option.
  - Native English UI across Appearance presets, `Follow System` toggle, live SQLite context capsule tooltips, and the `Token Usage Analytics` dashboard.
- **Claude-Style Compact Context Menus & Safe External IDE Bridge (PR #46)**:
  - Added theme-matched context menu cards across all 5 light and 3 dark surfaces for file pills, right-hand file lists, web links, code blocks, chat images (`Copy Image` / `Save Image`), and the composer (`Shift + Right-Click` native passthrough).
  - Added cached, disk-verified external IDE detection (`VS Code`, `Cursor`, `Windsurf`, `Zed`, `IntelliJ`, `PyCharm`, `WebStorm`, `GoLand`, `CLion`, `RustRover`, `Sublime Text`) and hardened `execFile` local browser/IDE bridges.
- **Antigravity `2.35.1` Compatibility**:
  - Includes all `v6.0.3` upstream enhancements: `Follow System` light/dark preset pairing, Windows 11 `TitleBarOverlay` & `--custom-window-controls` high-contrast adaptation, `260ms` metrics pill hover intent, and Remote SSH capsule auto-hide.
