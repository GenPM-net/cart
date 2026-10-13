# @core/cart

[![genpm](https://api.genpm.net/v1/badge/@core/cart.svg)](https://genpm.net/p/@core/cart) ![license](https://img.shields.io/badge/license-MIT-blue)

> Shopping cart: signed guest cookie, merge on login, server-side prices and a pluggable totals pipeline

A [GenPM](https://genpm.net) module: **source code + AI rules + MCP config**, injected into your project instead of hidden in `node_modules`. The code lands in `src/lib/cart`, pinned to a verified commit, and you own it.

## Install

```bash
genpm add @core/cart
```

No genpm yet? `curl -fsSL https://genpm.net/install.sh | sh` (macOS/Linux), `irm https://genpm.net/install.ps1 | iex` (Windows), or one-off with `npx @genpm-net/cli add @core/cart`.

Or let your AI agent do it: run `genpm mcp setup` once, then ask *"add @core/cart with genpm"* in Claude Code, Cursor, VS Code, Windsurf, Codex or Gemini CLI. It shows you a dry-run plan before writing anything.

## What it does

Carts for guests (id in an HMAC-signed HttpOnly cookie) and users (merged on login), lines per variant with stock
and quantity checks, and `computeTotals`: lines are always priced from @core/catalog in the database, unavailable
items are dropped with an `issues` entry, then registered steps run (discounts 100, shipping 200, taxes 300).
No payments or orders. Tables: `carts`, `cart_lines`.

## At a glance

- **GenPM dependencies** (installed with it): [@core/db](https://genpm.net/p/@core/db), [@core/auth](https://genpm.net/p/@core/auth), [@core/catalog](https://genpm.net/p/@core/catalog), [@core/money](https://genpm.net/p/@core/money), [@core/contracts](https://genpm.net/p/@core/contracts)
- **npm dependencies** (proposed, never installed without asking): `zod`
- **Environment variables** (added to `.env.example`): `CART_COOKIE_SECRET`
- **AI rules**: [`AGENTS.md`](AGENTS.md), loaded by your agent only when it works in `src/lib/cart`

## Security

GenPM installs a 40-character commit SHA (never a branch), verifies an Ed25519-signed manifest, never runs install scripts and scans AI rules for prompt injection. Details: [genpm.net/docs/security](https://genpm.net/docs/security).

## License

MIT — see [LICENSE](LICENSE). Browse the full catalog at [genpm.net](https://genpm.net).
