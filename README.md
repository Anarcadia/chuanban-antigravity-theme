# Chuanban Antigravity Theme (`v6.1.0` · Global Lightweight Edition)

> **Language Editions**: **English Lightweight Edition (Current)** · [简体中文完整汉化版 (`chuanban-antigravity-theme-patch`)](https://github.com/Anarcadia/chuanban-antigravity-theme-patch)

A non-invasive, warm-paper editorial theme, typography suite, compact context menu replacement, live context window capsule, and local SQLite Token Analytics dashboard for **Google Antigravity Desktop (`2.34.0` – `2.36.0+`)** across **macOS, Windows, and Linux**.

Built specifically as a **pure-English, ultra-lightweight parallel edition**:
- **Zero `.asar` Modification & Zero `npm` Dependencies**: Pure loopback CDP runtime injection — never touches `app.asar` and never breaks OS code signing.
- **Ultra-Light Footprint (`< 1 MB` Fonts or `0 MB` Native Mode)**: Physically omits the 68 KB CJK DOM translation observer and the 170–791 MB CJK font bundle. Only requires `< 1 MB` of `Anthropic Serif` & `Anthropic Mono` fonts (auto-downloaded via Cloudflare R2 / GitHub Release mirrors), or **`0 MB`** with `--font-mode native`.

---

## Key Features

1. **Seven-Preset Editorial & Flat Botanical Palettes + `Follow System` Pairing**
   - **Morandi Mineral (`MO` · Default)**: Warm Xuan-paper canvas paired with a crisp single-layer `2px` Slate-Mineral composer border (`#A3B5BA → #3D6470`).
   - **Meadow Inkstone (`🌱` · `meadow`) & Forest Night (`🌲` · `forest-night`)**: Fresh flat botanical light & dark skins featuring an imperceptible `256×256` lossless opaque limestone canvas (`#FAFBF9`) paired with an inkstone shell (`#E9EDE9`), `1px` forest-green composer, sans-serif prose (`Google Sans Flex`), 100% opaque menus, and crisp zero-ink-bleed rendering on Windows DirectWrite.
   - **Appearance Bar Switcher**: Switch instantly in **Settings → Appearance** across `[ A Original | ✳️ Absolutely! | MO Morandi | 🌱 Meadow Inkstone | 🌲 Forest Night | 📖 Warm Dark | 🌙 Dark ]` plus an independent **`Follow System`** light/dark auto-pairing toggle and Windows 11 `TitleBarOverlay` synchronization.

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

5. **Restrained, Non-Intrusive & Low-Risk Design**
   - Injects CSS styles exclusively into the frontend rendering layer via local loopback (`127.0.0.1`) CDP without unpacking or modifying `app.asar`, fully preserving official client digital signatures and OS notarization.
   - Built-in Token Analytics and the live metrics capsule strictly parse local on-disk SQLite session databases offline in read-only mode (`node:sqlite`), without reading system keychains or OAuth credentials, calling Google's internal private quota endpoints (such as `retrieveUserQuotaSummary`), or spoofing client identity headers (`User-Agent` / `clientInfo`), and without involving any CDP chat-flow automation, network proxy interception, multi-account switching, or cross-tool directory scanning (Note: while pure frontend runtime rendering-layer injection involves no network requests or credential interaction, it remains an unendorsed local modification gray area under literal client Terms of Service and is not zero-risk; supports one-command complete uninstallation and lossless restoration at any time).

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
- `user/custom.js` — sandboxed JS hooks (tag custom UI roots with `data-ag-plugin-ui="1"` for zero-overhead observer bypass).

---

## Community Add-ons (`user/` Layer · Optional)

Independent community extensions that install cleanly into `user/custom.{js,css}` via idempotent marker blocks (preserved across theme upgrades, zero `core/` or `.asar` changes, and natively adapted to all 5 Chuanban presets + English UI):

1. **Always-On Quota Bar & Pool Capsules** — [`ghang/ghang-antigravity-local-ui`](https://github.com/ghang/ghang-antigravity-local-ui) (by [@ghang](https://github.com/ghang))
   - Displays live Gemini weekly / 5h quota progress bars or compact rings above Settings in the left sidebar, plus auto-appearing top-bar capsules for independent quota pools (`Claude`, `GPT`, `Argon`) and detailed hover breakdowns.
   - **Install / Uninstall**: Clone the repo and run `node install.mjs install --json` (or `node install.mjs uninstall --json`).
2. **Sidebar "Recent (15)" Time-Grouped View & Collapsed Project Badges** — [`wysxxx/antigravity-sidebar-enhance`](https://github.com/wysxxx/antigravity-sidebar-enhance) (by [@wysxxx](https://github.com/wysxxx))
   - Adds a zero-height bell toggle in the Projects header to switch in-place to a single-line **Active / Today / Yesterday / Earlier** Recent view (with full native hover/context actions), plus aggregated pending/running/unread badges on collapsed project folders and independent switches in **Settings → Appearance**.
   - **Install / Uninstall**: Clone the repo and run `node install.mjs install --json` (or `node install.mjs uninstall --json`).

> *Disclaimer*: Community add-ons are independently maintained by their respective authors and read internal client React Fiber / Redux state at runtime. Run `node install.mjs verify --safe-mode` in this theme repository anytime to bypass `user/` scripts for troubleshooting.

## License

[MIT](./LICENSE)
