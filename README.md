# mtg-guides

Verified, clickable HTML strategy guides for Magic: The Gathering — **limited and constructed**.

- **Limited:** `docs/hobbit/` — The Hobbit (HOB) draft & sealed (5 archetypes, Storied/Recruit/Hone, prerelease kit) — Aug 12 2026 verified
- **Constructed:** `docs/standard-bo1-2026-08-13/` — Standard Best-of-One meta, 9 Arena-importable decks — Aug 13 2026 snapshot
- **Skill:** `skills/mtg-guide/SKILL.md` — reusable Pi/Hermes skill that built both guides (v0.2.0, not limited-specific)

## Browse

- Hobbit guide: [docs/hobbit/index.html](docs/hobbit/index.html) — `file:///…/docs/hobbit/index.html` or GitHub Pages
- Standard BO1 report: [docs/standard-bo1-2026-08-13/index.html](docs/standard-bo1-2026-08-13/index.html)
- Build status: `docs/hobbit/STATUS.md`, `docs/standard-bo1-2026-08-13/STATUS.md`

## Use the skill

```bash
# Pi discovers it as mtg-guide; also aliased as mtg-limited-guide (deprecated stub)
# Trigger: "build me a draft/sealed/standard BO1 guide for [set]"
```

Local build dirs: `~/projects/mtg-hobbit-guide/`, `~/projects/mtg-standard-bo1-report/` → published to `docs/` for Pages.

## Provenance

- Deep research job `msqe3uhv-znc85i7` (Hobbit, deep) fed the verified HOB build.
- Standard BO1 scraped live MTGGoldfish Aug 13 (2 days post-HOB Arena, provisional tiers).
- Hermes gateway flaked for the BO1 deep job — fell back to direct Goldfish scrape; re-run pending gateway fix.

*Fan content, not affiliated with Wizards of the Coast.*
