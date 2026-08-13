# mtg-guides

Verified, clickable HTML strategy guides for Magic: The Gathering — **limited and constructed**.

- **Limited:** `docs/hobbit/` — The Hobbit (HOB) draft & sealed (5 archetypes, Storied/Recruit/Hone, prerelease kit) — Aug 12 2026 verified
- **Constructed:** `docs/standard-bo1-2026-08-13/` — Standard Best-of-One meta, 8 Arena-importable decks (post-ban, S tier Mono-G/Spellementals) — Aug 13 2026 verified
- **Skill:** `skills/mtg-guide/SKILL.md` — reusable Pi/Hermes skill that built both guides (v0.2.0, not limited-specific)

## Browse — GitHub Pages

- **Landing:** [https://dweeb11.github.io/mtg-guides/](https://dweeb11.github.io/mtg-guides/) (resolves root; was 404 before `docs/index.html`)
- Hobbit guide: [https://dweeb11.github.io/mtg-guides/hobbit/](https://dweeb11.github.io/mtg-guides/hobbit/) — or [`docs/hobbit/index.html`](docs/hobbit/index.html) / `file:///…/docs/hobbit/index.html`
- Standard BO1 report: [https://dweeb11.github.io/mtg-guides/standard-bo1-2026-08-13/](https://dweeb11.github.io/mtg-guides/standard-bo1-2026-08-13/) — or [`docs/standard-bo1-2026-08-13/index.html`](docs/standard-bo1-2026-08-13/index.html)
- Build status: `docs/hobbit/STATUS.md`, `docs/standard-bo1-2026-08-13/STATUS.md`

## Use the skill

```bash
# Pi discovers it as mtg-guide; also aliased as mtg-limited-guide (deprecated stub)
# Trigger: "build me a draft/sealed/standard BO1 guide for [set]"
```

Local build dirs: `~/projects/mtg-hobbit-guide/`, `~/projects/mtg-standard-bo1-report/` → published to `docs/` for Pages.

## Provenance

- Deep research job `msqe3uhv-znc85i7` (Hobbit, deep) fed the verified HOB build.
- Standard BO1 verified via `msrscmk9-5vx1l6d` (gpt-5.6-sol deep, Nous Firecrawl, delivered Aug 13 10:29 PT) — 8 post-ban 60s + Challenges Aug 11/13 + Untapped 110k + Wizards B&R Aug 10 (fell back to live MTGGoldfish scrape Aug 13 when gateway was `invalid_grant`; gateway fixed Aug 13 10:21 `nous ✓`).

*Fan content, not affiliated with Wizards of the Coast.*
