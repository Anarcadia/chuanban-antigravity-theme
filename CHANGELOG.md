# Changelog

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
