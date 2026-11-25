# Chuanban Antigravity Theme (`v6.0.4` · Global Lightweight Edition)

> **Language Editions**: **English Lightweight Edition (Current)** · [简体中文完整汉化版 (`chuanban-antigravity-theme-patch`)](https://github.com/Anarcadia/chuanban-antigravity-theme-patch)

A non-invasive, warm-paper editorial theme, typography suite, compact context menu replacement, live context window capsule, and local SQLite Token Analytics dashboard for **Google Antigravity Desktop (`2.34.0` – `2.35.2+`)** across **macOS, Windows, and Linux**.

Built specifically as a **pure-English, ultra-lightweight parallel edition**:
- **Zero `.asar` Modification & Zero `npm` Dependencies**: Pure loopback CDP runtime injection — never touches `app.asar` and never breaks OS code signing.
- **Ultra-Light Footprint (`< 1 MB` Fonts or `0 MB` Native Mode)**: Physically omits the 68 KB CJK DOM translation observer and the 170–791 MB CJK font bundle. Only requires `< 1 MB` of `Anthropic Serif` & `Anthropic Mono` fonts (auto-downloaded via Cloudflare R2 / GitHub Release mirrors), or **`0 MB`** with `--font-mode native`.

---

## Key Features

1. **Five-Preset Warm-Paper Palette & `Follow System` Pairing**
   - **Morandi Mineral (Default)**: Warm Xuan-paper canvas paired with a crisp single-layer `2px` Slate-Mineral composer border (`#A3B5BA → #3D6470`).
   - **Appearance Bar Switcher**: Switch instantly in **Settings → Appearance** between `[ A Original | ✳️ Absolutely! | MO Morandi | 📖 Warm Dark | 🌙 Dark ]` plus an independent **`Follow System`** light/dark auto-pairing toggle.
   - Full Windows 11 `TitleBarOverlay` & `--custom-window-controls` high-contrast synchronization.

2. **Editorial Three-Layer Typography**
   - **UI Controls**: Native variable `Google Sans Flex` with optical weight balancing.
   - **Chat & Markdown Prose**: `Anthropic Serif` for long-form reading comfort (or native sans-serif via `"fontMode": "native"`).
   - **Code, Inline File Pills & Composer**: `Anthropic Mono`.

3. **Claude-Inspired Compact Context Menu & Safe External IDE Bridge**
   - Replaces jarring OS-native context menus in chat, code blocks, links, images, file pills, and the composer with theme-matched compact cards (`Shift + Right-Click` always passes through to the native menu).
   - Automatically detects genuinely installed external IDEs on disk (`VS Code`, `Cursor`, `Windsurf`, `Zed`, `JetBrains IDEs`, `Sublime Text`) and safely opens local `.html / .pdf / .svg` previews in your default browser.

4. **Live Context Telemetry Capsule & Local Token Analytics (`node:sqlite`)**
   - Real-time context window progress bar, token/s speed, TTFT, and cache hit tooltip right below the composer (including split panes & `/btw` side tabs; auto-hides on Remote SSH when no local DB exists).
   - **Settings → Local Extensions → Token Analytics**: Local-only SQLite attribution across 26-week activity heatmaps, models/quota pools, scenarios, projects, and expandable subagent trees.

---

## Quick Install (AI-Agent Guided or Manual CLI)

**Requirements**: **Node.js `>= 22.13.0`** recommended (`>= 22.0.0` minimum).

### Option A: One-Prompt Install via AI Agent (Antigravity / Claude Code / Codex)
Paste into your agent:
> Read `SKILL.md` in this repository and install `chuanban-antigravity-theme` for me.

### Option B: Manual 3-Command CLI Install
```bash
# 1. Check environment & auto-download <1 MB Anthropic Serif/Mono fonts (skip if using --font-mode native)
node install.mjs doctor
node install.mjs install-fonts --auto-download

# 2. Install theme core & register background daemon (pass --font-mode native for 0 MB zero-font mode)
node install.mjs install

# 3. Verify live window injection
node install.mjs verify
```

---

## Hot-Reload Customization (`2.5s`)

All personal settings live in `~/.gemini/antigravity/theme-patch/user/` (`%USERPROFILE%\.gemini\antigravity\theme-patch\user\` on Windows) and are never overwritten on upgrade:
- `user/config.json` — switch `preset`, `darkPreset`, `fontMode` (`"anthropic"` | `"native"`), `--ag-chat-font-size`, or toggle individual `modules` (`metrics`, `tokenAnalytics`, `contextMenu`, `composerWaxSeal`).
- `user/custom.css` — custom CSS overrides.
- `user/custom.js` — sandboxed JS hooks.

## License

[MIT](./LICENSE)
