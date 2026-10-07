<p align="center">
  <img src="docs/images/logo.svg" width="72" height="72" alt="Cephalon Cuda mark">
</p>

<h1 align="center">Cephalon Cuda</h1>

<p align="center"><strong>Windows Warframe companion for new, active, and returning players.</strong></p>

<p align="center">
  Turns scattered systems into a practical decision layer: what to do next, what to build, where an item comes from, whether an old build is still worth investing in, and which Platinum purchases are traps.<br>
  Offline-first. Personal state stays in local SQLite. Public game data refreshes into a source-stamped knowledge layer.
</p>

<p align="center">
  <a href="https://github.com/SenjuWoo/Cephalon-Cuda/actions/workflows/ci.yml"><img src="https://github.com/SenjuWoo/Cephalon-Cuda/actions/workflows/ci.yml/badge.svg" alt="CI"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-65f4e8?labelColor=03080a" alt="MIT License"></a>
  <a href="https://github.com/SenjuWoo/Cephalon-Cuda/releases/tag/v2.2.0"><img src="https://img.shields.io/badge/release-v2.2.0-47cbff?labelColor=03080a" alt="v2.2.0"></a>
</p>

<p align="center">
  <a href="https://github.com/SenjuWoo/Cephalon-Cuda/releases/latest">Download</a>
  ·
  <a href="#quick-start">Quick start</a>
  ·
  <a href="#privacy-and-game-safety">Privacy and game safety</a>
  ·
  <a href="CHANGELOG.md">Changelog</a>
</p>

## Quick start

Latest release: **[v2.2.0](https://github.com/SenjuWoo/Cephalon-Cuda/releases/tag/v2.2.0)** (`Cephalon_Cuda_2.2_Nexus_Release.zip`).

1. Extract **anywhere outside Program Files**.
2. Run `CephalonCuda.exe`.
3. Complete first-run setup.
4. Add an OpenRouter key **only** if you want AI Advisor.

Runtime: 64-bit Windows 10 or 11, WebView2 for the embedded advisor panel, internet for live data. Borderless or Windowed Warframe for overlay and capture features.

Local data lives under `%LocalAppData%\CephalonCuda`. Uninstall by deleting the EXE; delete that folder only if you also want settings, caches, and encrypted API credentials gone.

## Return Protocol

**Just Got Back?** uses trustworthy local activity from `EE.log`, remembers the previous session gap, and builds a controlled re-entry plan instead of dumping every new system on the player.

It prioritizes ready Foundry claims, the next unresolved roadmap objective, the player’s goals, unclaimed redemption codes, stale data sources, old builds that need revalidation, and live time-limited opportunities.

Return state is **never fabricated** from inaccessible account data. Confirm play activity manually, edit goals, and control automatic briefings.

## What you get

- Live Overview, Tenno Path / Return Protocol
- Inventory and disposition checks
- Relic Planner with expected-value ranking and OCR
- Market & Trading (orders, history, ledger, listing sync)
- Mastery Helper, Foundry timers, Riven Assistant
- Live Data & Intel health dashboard
- Streaming AI Advisor
- Overlay HUD, capture, OCR, Immersive Mode
- Shop Guardian against poor-value Platinum spends
- Eight full-interface palettes (Verv, Lotus, Orokin, Entrati, Corpus, Grineer, Void, High Contrast)

## Privacy and game safety

Cephalon Cuda does **not** read game memory, inject code, automate input, or play the game. It uses read-only `EE.log` events, visual capture/OCR, public endpoints, and information entered or confirmed by the user.

See [`PRIVACY_AND_DATA.md`](PRIVACY_AND_DATA.md).

## Honest status

Verified in this tree:

- Release build with warnings treated as errors
- Full UI `--smoke` cycle (all themes / workspaces)
- Live `--verify-data` schema + integrations
- Offline validation contracts in [`VALIDATION_REPORT.md`](VALIDATION_REPORT.md)

Not claimed:

- Visibility into private account progression Digital Extremes does not expose
- That community build votes or tiers are truth — they remain source-stamped opinions
- An automated Overframe scraper (not shipped; see `docs\COMMUNITY_INTEL_SCHEMA.md`)

## Build the verified release

On 64-bit Windows 10 or 11 with the .NET 8 SDK:

```bat
BUILD_V2.2.bat
```

The pipeline restores, builds Release with warnings as errors, publishes a self-contained `win-x64` executable, runs `--smoke` and `--verify-data`, then writes Nexus and Source folders under `dist`. A failed build, smoke test, or live verification stops the pipeline before packaging.

```bat
run.bat
publish.bat
```

```bat
publish\CephalonCuda.exe --smoke
publish\CephalonCuda.exe --verify-data
```

Reports and crash logs: `%LocalAppData%\CephalonCuda\logs`.

## Credits

Warframe, Tenno, and related names are trademarks of Digital Extremes. This project is unofficial. Third-party notices: [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md).

## License

[MIT](LICENSE)

## Notes in 2.2

- Automatic intelligence pipeline with per-source freshness windows; a failed refresh never deletes the last valid database
- Evidence-aware build synthesis (item stats, licensed/imported community builds, acquisition routes, market context, player goals)
- Runtime theme replacement across already-open views
- R3.1 hotfix: theme metrics used as `GridLength` must actually be `GridLength`, or startup fails
