# ApexFlow

English | [简体中文](README.zh-CN.md)

Proxy-related config repo for the phone (Shadowrocket + Loon), plus Tailscale DERP direct rules and CN-reliable mirrors. Public by design — **no subscription links, no keys, no private host info**.

## Files

| File | What it is | Fetched from |
|---|---|---|
| `ApexFlow.conf` | Shadowrocket phone config (current) | Pages (config's own `update-url`) — in-app「更新配置」 |
| `ApexFlow-Loon.conf` | Loon phone config (current, ≥3.5.4 for the Tailscale node type) | Pages — import once, in-app「更新」later |
| `ApexFlow_backup` | Previous Shadowrocket config (v7), emergency rollback | — |
| `{{TERM_b4cqz2lbz}}-derp-direct.list` / `.yaml` | Tailscale DERP server IP direct rules, referenced via `RULE-SET` | jsDelivr |
| `vendor/` | Mirrors of third-party assets (Sub-Store parser, iRingo WeatherKit) so Loon can fetch them reliably from mainland networks | Pages |

## Usage

- **Shadowrocket**: add `ApexFlow.conf` as a remote config; its `update-url` points at this repo (GitHub Pages), so in-app updates pull changes directly.
- **Loon**: import `ApexFlow-Loon.conf` from Pages. Config and subscription are separated: the airport sub lives at app level (add once in the「订阅」page with the Sub-Store parser enabled), config updates never touch it.
- This repo is served via **GitHub Pages** (`isai129.github.io/ApexFlow/...`) — jsDelivr's branch cache proved unreliable for @main, and raw.githubusercontent is blocked on mainland cellular. Rule-set URLs still use jsDelivr (stable upstream repos).

## Notes

- `{{TERM_b4cqz2lbz}}-derp-direct.list` is regenerated weekly from the live DERPMap by a script on the home server (DERP IPs rotate; a static list goes stale). Manual edits get overwritten.
- `vendor/` files are unmodified third-party releases except for URL rewrites inside `iRingo.WeatherKit.lpx` (script-path → local mirrors). Re-download + re-apply on upstream updates.
- Split from the private `SR_Conf` repo on 2026-11-02; SR_Conf keeps mihomo/host config templates and mirrors.
